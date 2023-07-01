# DSA-Basic-2
QUESTION 6:-
METHOD 1:-
 
def isOperator(x):
 
    if x == "+":
        return True
 
    if x == "-":
        return True
 
    if x == "/":
        return True
 
    if x == "*":
        return True
 
    return False
 
# Convert postfix to Prefix expression
 
 
def postToPre(post_exp):
 
    s = []
 
    # length of expression
    length = len(post_exp)
 
    # reading from right to left
    for i in range(length):
 
        # check if symbol is operator
        if (isOperator(post_exp[i])):
 
            # pop two operands from stack
            op1 = s[-1]
            s.pop()
            op2 = s[-1]
            s.pop()
 
            # concat the operands and operator
            temp = post_exp[i] + op2 + op1
 
            # Push string temp back to stack
            s.append(temp)
 
        # if symbol is an operand
        else:
 
            # push the operand to the stack
            s.append(post_exp[i])
 
    
    ans = ""
    for i in s:
        ans += i
    return ans
 
 
# Driver Code
if __name__ == "__main__":
 
    post_exp = "AB+CD-"
     
    # Function call
    print("Prefix : ", postToPre(post_exp))


 
def isOperator(x):
 
    if x == "+":
        return True
 
    if x == "-":
        return True
 
    if x == "/":
        return True
 
    if x == "*":
        return True
 
    return False
 
# Convert postfix to Prefix expression
 
 
def postToPre(post_exp):
 
    s = []
 
    # length of expression
    length = len(post_exp)
 
    # reading from right to left
    for i in range(length):
 
        # check if symbol is operator
        if (isOperator(post_exp[i])):
 
            # pop two operands from stack
            op1 = s[-1]
            s.pop()
            op2 = s[-1]
            s.pop()
 
            # concat the operands and operator
            temp = post_exp[i] + op2 + op1
 
            # Push string temp back to stack
            s.append(temp)
 
        # if symbol is an operand
        else:
 
            # push the operand to the stack
            s.append(post_exp[i])
 
    
    ans = ""
    for i in s:
        ans += i
    return ans
 
 
# Driver Code
if __name__ == "__main__":
 
    post_exp = "AB+CD-"
     
    # Function call
    print("Prefix : ", postToPre(post_exp))


QUESTION 7:-

def prefixToInfix(prefix):  
    symbols = []  
       
    # reading the prefix string  
    l = len(prefix) - 1  
    while l >= 0:  
        if not Operator(prefix[l]):  
               
            # The current symbol is an operand  
            symbols.append(prefix[l])  
            l -= 1  
        else:  
             
            # the current symbol is an operator  
            string = "(" + symbols.pop() + prefix[l] + symbols.pop() + ")"  
            symbols.append(string)  
            l -= 1  
       
    return symbols.pop()  
  
def Operator(symbols):  
    if symbols == "*" or symbols == "+" or symbols == "-" or symbols == "/" or symbols == "^" or symbols == "(" or symbols == ")":  
        return True  
    else:  
        return False  
  
# Calling the function  
string = "*+P/QR-/STU"  
print("The infix string is: ", prefixToInfix(string))  
 
METHOD 2:-
def prefixToInfix(prefix):
    stack = []
     
    # read prefix in reverse order
    i = len(prefix) - 1
    while i >= 0:
        if not isOperator(prefix[i]):
             
            # symbol is operand
            stack.append(prefix[i])
            i -= 1
        else:
           
            # symbol is operator
            str = "(" + stack.pop() + prefix[i] + stack.pop() + ")"
            stack.append(str)
            i -= 1
     
    return stack.pop()
 
def isOperator(c):
    if c == "*" or c == "+" or c == "-" or c == "/" or c == "^" or c == "(" or c == ")":
        return True
    else:
        return False
 
# Driver code
if __name__=="__main__":
    str = "*-A/BC-/AKL"
    print(prefixToInfix(str))



QUESTION 8:-
METHOD 1:-

def paraCheck( seq ):  
   while True:  
       if '()' in seq :  
           seq = seq.replace ( '()' , '' )  
       elif '{}' in seq :  
           seq = seq.replace ( '{}' , '' )  
       elif '[]' in seq :  
           seq = seq.replace ( '[]' , '' )  
       else :  
           return not seq  
  
seq = '{[()]}'  
print(f'Is {seq} valid ? : {paraCheck(seq)}')  
seq1 = '{[()]}{]{}}'  
print(f'Is {seq1} valid ? : {paraCheck (seq1)}')  

METHOD 2:-
class Solution:
   def isValid (self, sequence: str):
       '''
       Function to pair if sequence contains valid parenthesis
       :param sequence: Sequence of brackets
       :return: True is sequence is valid else False
       '''
       stack = []
       opening = set('([{')
       closing = set(')]}')
       pair = {')' : '(' , ']' : '[' , '}' : '{'}
       for i in sequence :
           if i in opening :
               stack.append(i)
           if i in closing :
               if not stack :
                   return False
               elif stack.pop() != pair[i] :
                   return False
               else :
                   continue
       if not stack :
           return True
       else :
           return False

if __name__ == '__main__':
   sequence = '{[()]}'
   print(f'Is {sequence} valid ? : {Solution().isValid(sequence)}')
   sequence1 = '{[()]}{]{}}'
   print(f'Is {sequence1} valid ? : {Solution().isValid (sequence1)}')

METHOD 3:-
open_list = ["[","{","("]
close_list = ["]","}",")"]
 
# Function to check parentheses
def check(myStr):
    stack = []
    for i in myStr:
        if i in open_list:
            stack.append(i)
        elif i in close_list:
            pos = close_list.index(i)
            if ((len(stack) > 0) and
                (open_list[pos] == stack[len(stack)-1])):
                stack.pop()
            else:
                return "Unbalanced"
    if len(stack) == 0:
        return "Balanced"
    else:
        return "Unbalanced"
 
 
# Driver code
string = "{[]{()}}"
print(string,"-", check(string))
 
string = "[{}{})(]"
print(string,"-", check(string))
 
string = "((()"
print(string,"-",check(string))

QUESTION 9:-
class Stack:
    def __init__(self):
        self.items = []
 
    def is_empty(self):
        return self.items == []
 
    def push(self, data):
        self.items.append(data)
 
    def pop(self):
        return self.items.pop()
 
    def display(self):
        for data in reversed(self.items):
            print(data)
 
def insert_at_bottom(s, data):
    if s.is_empty():
        s.push(data)
    else:
        popped = s.pop()
        insert_at_bottom(s, data)
        s.push(popped)
 
 
def reverse_stack(s):
    if not s.is_empty():
        popped = s.pop()
        reverse_stack(s)
        insert_at_bottom(s, popped)
 
 
s = Stack()
data_list = input('Please enter the elements to push: ').split()
for data in data_list:
    s.push(int(data))
 
print('The stack:')
s.display()
reverse_stack(s)
print('After reversing:')
s.display()


METHOD 2:-

class Stack_structure:
   def __init__(self):
      self.items = []

   def check_empty(self):
      return self.items == []

   def push_val(self, data):
      self.items.append(data)

   def pop_val(self):
      return self.items.pop()

   def print_it(self):
      for data in reversed(self.items):
         print(data)

def insert_bottom(instance, data):
   if instance.check_empty():
      instance.push_val(data)
   else:
      deleted_elem = instance.pop_val()
      insert_bottom(instance, data)
      instance.push_val(deleted_elem)

def stack_reverse(instance):
   if not instance.check_empty():
      deleted_elem = instance.pop_val()
      stack_reverse(instance)
      insert_bottom(instance, deleted_elem)

my_instance = Stack_structure()
data_list = input('Enter the elements to add to the stack: ').split()
for data in data_list:
   my_instance.push_val(int(data))

print('The reversed stack is:')
my_instance.print_it()
stack_reverse(my_instance)
print('The stack is:')
my_instance.print_it()


QUESTION 10:-
class MinStack(object):
   min=float('inf')
   def __init__(self):
      self.min=float('inf')
      self.stack = []
   def push(self, x):
      if x<=self.min:
         self.stack.append(self.min)
         self.min = x
      self.stack.append(x)
   def pop(self):
      t = self.stack[-1]
      self.stack.pop()
      if self.min == t:
         self.min = self.stack[-1]
         self.stack.pop()
   def top(self):
      return self.stack[-1]
   def getMin(self):
      return self.min
m = MinStack()
m.push(-2)
m.push(0)
m.push(-3)
print(m.getMin())
m.pop()
print(m.top())
print(m.getMin())


METHOD 2:-
arr = [25, 11, 7, 75, 56];     
     
#Initialize min with the first element of the array.    
    
min = arr[0];    
     
#Loop through the array    
for i in range(0, len(arr)):    
    #Compare elements of array with min    
   if(arr[i] < min):    
       min = arr[i];    
     
print("Smallest element present in given array: " + str(min));    


METHOD 3:-
smallest element in list

#function
def smallest(list):
    small= list[0]
    for i in list:
        if i<small:
            small=i
    return small

#list
list=[3, 9, 7, 3, 6, 5, 7, 24, 6]
print("smallest in ",list,"is")
print(smallest(list))





