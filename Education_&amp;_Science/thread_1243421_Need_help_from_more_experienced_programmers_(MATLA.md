---
title: "Need help from more experienced programmers (MATLAB)"
date: 2009-08-18
forum: Education &amp; Science
---

### Post by lethalfang on 2009-08-18
I've started learning to program a little over 6 months ago to solve problems, and I have this problem that I don't quite have a programming strategy for in MATLAB. 

I wrote a function that takes one input and outputs 2 answers, i.e., [out1, out2] = f(x). I want to put those 2 answers to the same function which will output 4 answers, which will be put into the same function again, and so forth. 

How do I do that?

Thanks.

---

### Post by XCan on 2009-08-18
Interesting, although I haven't been in need of anything similar. Without thinking too hard, I would probably go for to store everything in a cell structure as follows:

```

1) data{1} = x;
2) data = f(data);
3) f loops through 1 to length(data), for each loop assigns two new cells into some other cell variable which is returned.
4) repeat from 2). 

```

Disclaimer: This of course won't give the best speed, but it's quite intuitive, for speed, consider preallocating a matrix and store the output there instead if possible.

---

### Post by lethalfang on 2009-08-18
Thanks for pointing me toward cell as a data tyle. I've never used that before and was not aware it. I'll need to spend a little more time working on it, but it seems like a feasible approach. 
Since my outputs are vectors, but the number of entries in the vectors gets shorter after each cycle (in an unpredictable and irregular fashion), it is a little problematic for me trying to store those data into a matrix because a matrix only takes vectors of equal size.

---

### Post by XCan on 2009-08-18
You're welcome. Yah, if you are returning stuff with different sizes cells are far more easier to work with indeed.

---

### Post by riazrahaman on 2009-08-20
From where did you download matlab? Couldn't find in synaptic though

---

### Post by XCan on 2009-08-20
Matlab is properiatary. [http://www.mathworks.com/](http://www.mathworks.com/)

---

### Post by lethalfang on 2009-08-28
> **riazrahaman said:**
> From where did you download matlab? Couldn't find in synaptic though

If you want something similar to MATLAB, try Octave. It can do most of what MATLAB does (i.e., the codes are 95% compatible with each other), but not all.

---

### Post by sprince09 on 2009-08-28
I second Octave. I've pretty much entirely switched to Octave from MATLAB... Simulink is the only reason I still have MATLAB kicking around on my drive.

---

### Post by elbarto_87 on 2009-09-02
Your problem sounds like a recursive problem. I have written a small example of a recursive function that is similar to what you are looking for (Not the best solution but its small and works).

I wanted a function that would reverse an array of numbers.

```
function foo =  recursiveFoo(myarray)
    if isempty(whos('foo'));foo = [];end%make veriable if it doesn't exist
    tmp = myarray(end);%get last entry
    myarray(end) = [];%delete last entry
    if ~isempty(myarray)%if the array isnt empty
        foo = [tmp recursiveFoo(myarray)];%call calling function again
    else
        foo = tmp;%establish base case
    end
    
```

Example:

```
EDU>> recursiveFoo(1:5)

ans =

     5     4     3     2     1

EDU>> 
```

Im not sure what your level of programming experience is but I have only recently learned a little about recursion and have found it to be useful for these kind of problems. Maybe if you added a little more about your problem someone could provide a less general solution.

Regards Elbarto

---

### Post by XCan on 2009-09-02
Recursive functions can indeed be very easy to deal with. However, aren't they (especially in Matlab) associated with very poor performance in many languages?

---

### Post by elbarto_87 on 2009-09-03
I think it would depend on what problem you are trying to solve. I do not think reversing a list with recursion would be any slower then useing a loop but it does have limitations such as the maximum recursion depth which you need to be mindful of if you need to change it for larger problems.

Something like calculating the nth Fibonacci number using recursion would probably be much slower than useing a loop? 

I am not very experienced with recursion nor am I an "experienced" programmer so I make no claim that my thoughts above are accurate.

XCan, your method of using a cell array is probably a more favorable method, but depending on that actual problem the OP was trying to solve I thought establishing a single base case and using recursion could possibly simplify the problem considerably as you mentioned.

Regards Elbarto

---

### Post by bzm3r on 2009-09-03
Recursion in general is slower than doing things using a loop, or your own stack structure, as a recursive program is merely using the OS's stack to do its work. So if you care about speed (for example when a large number of recursive calls need to be made), avoid it. 

However, for some problems, it can be very intuitive to use recursion, making it an ideal choice for quick programming.

But I do agree with elbarto, I think this program could be written recursively.

--- start of function ---
function [out1, out2] = f(x)
    function body
    ""
....

   f(out1) 
   f(out2)

--- end of function ---

---

### Post by elbarto_87 on 2009-09-05
I find the concept of recursion quite intriguing with some of the solutions it can yield rather easily. For example:
[URL="http://en.wikipedia.org/wiki/Tower_of_Hanoi"]
 http://en.wikipedia.org/wiki/Tower_of_Hanoi[/URL]

Regards Elbarto

---

### Post by XCan on 2009-09-05
There is nothing wrong with recursion, I didn't mean to imply that. I just meant that it should not always be thought as the solution due to its performance issues. But for small problems, or problems where speed does not matter that much, when you have a choice to save tons of time using a recursive function, of course you should go for it. :)

---

### Post by jpkotta on 2009-09-11
In octave:
```

function ret = nest(func, arg, n)
    ret = arg;
    for i = 1:n
        ret = func(ret);
    end
endfunction

nest(@(x) [x,x], 0, 3) % returns the same as zeros(1,2^3)

```

---

