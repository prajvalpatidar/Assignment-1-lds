Q1. Write a program to find all pairs of an integer array whose sum is equal to a given number?
ans: function printPairs(arr, n, sum)
{
    let count = 0;
      for (let i = 0; i < n; i++)
        for (let j = i + 1; j < n; j++)
            if (arr[i] + arr[j] == sum)
                 document.write("(" + arr[i] + ", "
                    + arr[j] + ")" + "<br>");
}
    let arr = [ 1, 5, 7, -1, 5 ];
    let n = arr.length;
    let sum = 6;
    printPairs(arr, n, sum);
    
    output
    (1, 5)
    (1, 5)
    (7, -1)
 
 Q2. Write a program to reverse an array in place? In place means you cannot create a new array. You have to update the original array.
 ans: reverseArray = arr =>{
      newArr = []
      arr.forEach(element => {
      newArr.unshift(element)
      })
      return newArr
      }
      reverseArray([1,2,3,4,5]);
      
      output
      [5,4,3,2,1]
      
Q3. Write a program to check if two strings are a rotation of each other?  
ans: function areRotations( str1,  str2)
    {
        // There lengths must be same and str2 must be
        // a substring of str1 concatenated with str1. 
        return (str1.length == str2.length) &&
               ((str1 + str1).indexOf(str2) != -1);
    }
     
    // Driver method
 
        var str1 = "AACD";
        var str2 = "ACDA";
 
        if (areRotations(str1, str2))
            document.write("Strings are rotations of each other");
        else
            document.write("Strings are not rotations of each other");
            
       output
       Strings are rotations of each other
       
Q4. Write a program to print the first non-repeated character from a string?   
ans: function firstNonRepeating(str)
{
    var fi=new Array(256);
     
    fi.fill(-1);
 
    for(var i = 0; i<256; i++)
        fi[i] = -1;
 
    for(var i = 0; i<str.length; i++)
    {
        if(fi[str.charCodeAt(i)] ==-1)
        {
            fi[str.charCodeAt(i)] = i;
             
        }
        else
        {
            fi[str.charCodeAt(i)] = -2;
        }
    }
 
    var res = Infinity;
 
    for(var i = 0; i<256; i++) {
 
        if(fi[i] >= 0)
            res = Math.min(res, fi[i]);
    }
     
    if(res == Infinity) return -1;
    else return res;
  }
 
   var str;
    str = "geeksforgeeks";
    var firstIndex = firstNonRepeating(str);
    if (firstIndex === -1)
        document.write("Either all characters are repeating or string is empty");
    else
        document.write("First non-repeating character is "+ str.charAt(firstIndex));
        
        output
        First non-repeating character is f
        
Q5. Read about the Tower of Hanoi algorithm. Write a program to implement it?
ans: function towerOfHanoi(n, from_rod,  to_rod,  aux_rod)
     {
        if (n == 1)
        {
            document.write("Move disk 1 from rod " + from_rod +
            " to rod " + to_rod+"<br/>");
            return;
        }
        towerOfHanoi(n - 1, from_rod, aux_rod, to_rod);
        document.write("Move disk " + n + " from rod " + from_rod +
        " to rod " + to_rod+"<br/>");
        towerOfHanoi(n - 1, aux_rod, to_rod, from_rod);
     }
 
     var n = 4; 
     towerOfHanoi(n, 'A', 'C', 'B');
     
     output
     Move disk 1 from rod A to rod B
     Move disk 2 from rod A to rod C
     Move disk 1 from rod B to rod C
     Move disk 3 from rod A to rod B
     Move disk 1 from rod C to rod A
     Move disk 2 from rod C to rod B
     Move disk 1 from rod A to rod B
     Move disk 4 from rod A to rod C
     Move disk 1 from rod B to rod C
     Move disk 2 from rod B to rod A
     Move disk 1 from rod C to rod A
     Move disk 3 from rod B to rod C
     Move disk 1 from rod A to rod B
     Move disk 2 from rod A to rod C
     Move disk 1 from rod B to rod C
     
Q6. Read about infix, prefix, and postfix expressions. Write a program to convert postfix to prefix expression.     
ans:  function isOperator(x)
    {
        switch (x) {
        case '+':
        case '-':
        case '/':
        case '*':
            return true;
        }
        return false;
    }
     
    // Convert prefix to Postfix expression
    function preToPost(pre_exp)
    {
  
        let s = [];
  
        // length of expression
        let length = pre_exp.length;
  
        // reading from right to left
        for (let i = length - 1; i >= 0; i--)
        {
  
            // check if symbol is operator
            if (isOperator(pre_exp[i]))
            {
                // pop two operands from stack
                let op1 = s[s.length - 1];
                s.pop();
                let op2 = s[s.length - 1];
                s.pop();
  
                // concat the operands and operator
                let temp = op1 + op2 + pre_exp[i];
  
                // Push String temp back to stack
                s.push(temp);
            }
  
            // if symbol is an operand
            else {
                // push the operand to the stack
                s.push(pre_exp[i] + "");
            }
        }
  
        // stack contains only the Postfix expression
        return s[s.length - 1];
    }
     
    let pre_exp = "*-A/BC-/AKL";
    document.write("Postfix : " + preToPost(pre_exp));
     
     output
     Postfix : ABC/-AK/L-*
     
Q7. Write a program to convert prefix expression to infix expression?.
ans: function isOperator(x)
    {
        switch(x)
        {
            case '+':
            case '-':
            case '*':
            case '/':
                return true;
        }
        return false;
    }
 
   
    function convert(str)
    {
        let stack = [];
 
        let l = str.length;

        for(let i = l - 1; i >= 0; i--)
        {
            let c = str[i];
 
            if (isOperator(c))
            {
                let op1 = stack[stack.length - 1];
                stack.pop()
                let op2 = stack[stack.length - 1];
                stack.pop()

                let temp = "(" + op1 + c + op2 + ")";
                stack.push(temp);
            }
            else
            {
 
                stack.push(c + "");
            }
        }
        return stack[stack.length - 1];
       }
     
       let exp = "*-A/BC-/AKL";
      
       document.write("Infix : " + convert(exp));
       
       Output: Infix : ((A-(B/C))*((A/K)-L))
      
