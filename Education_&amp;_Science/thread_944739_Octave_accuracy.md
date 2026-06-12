---
title: "Octave accuracy"
date: 2008-10-11
forum: Education &amp; Science
---

### Post by Nonplay on 2008-10-11
Using Octave I have:

```
octave:1> x = [5 2 2; 4 32 1]
x =

    5    2    2
    4   32    1

octave:2> x/x
ans =

   1.0000e+00   3.4520e-18
   3.5764e-16   1.0000e+00


```

The more precise answer should be: 

```

ans =

   1   0
   0   1


```
and this is the answer that you have running the same case
in other programs such as Freemat and Matlab.

Do you think that is it a problem caused by the less precision in the algorithm used by octave, or I should report this case as a bug on octave's website?

Thank to all
Np

---

### Post by BillN1VUX on 2008-10-11
At first glance it appears Octave matrices are born Double precision float even if all entries are integers. You may need to invoke int32 conversion.

[http://www.gnu.org/software/octave/doc/interpreter/Integer-Data-Types.html#Integer-Data-Types](http://www.gnu.org/software/octave/doc/interpreter/Integer-Data-Types.html#Integer-Data-Types)

[http://www.google.com/search?hl=en&q=octave+integer-division](http://www.google.com/search?hl=en&q=octave+integer-division)

Also Octave rounds not trunc or floor inmost cases so be aware.

---

### Post by WW on 2008-10-11
Matlab shows similar results, if you look more closely:
```

>> x = [5 2 2; 4 31 1]
x =
     5     2     2
     4    31     1
>> x/x
ans =
    1.0000    0.0000
    0.0000    1.0000
>> format long e
>> x/x
ans =
     9.999999999999998e-01     1.907131576043213e-17
     1.118373745381119e-17     1.000000000000000e+00
>>

```

EDIT: Oops... as ahmatti points out below, I used the wrong matrix in that example.  The exact result should still be [1 0; 0 1], but it is not an apples-to-apples comparison.

Even with the same matrix, matlab does not give the exact answer.  The output format might make it look exact, as in ahmatti's post below.  These commands show that matlab does not give the exact value for the zero in the lower left entry:
```

>> x = [5 2 2; 4 32 1]
x =
     5     2     2
     4    32     1
>> b = x/x
b =
    1.0000         0
    0.0000    1.0000
>> format long
>> b(1,1)
ans =
     1
>> b(2,1)
ans =
     1.919911137851190e-16
>> b(1,2)
ans =
     0
>> b(2,2)
ans =
     1
>> 

```
I don't know if it is just luck that matlab gets the other three entries exact, or if the matlab algorithm does a better job than octave of minimizing floating point errors. My first example (with 31 instead of 32) shows that, in general, matlab will not give the exact answer for such a calculation.

I should also add that I am using an older version of matlab (R2006a).

---

### Post by smattiuz on 2008-10-29
Every computer can represent a finite set of real numbers, the "machine numbers" (a single precision,float, occupies 32 bits, a double precision, double, 32+32 bits)

Any normal number is represented like this
> x = (&#8722;1)^S · 2^(E &#8722;bias) · (1.F + &#948;)

where
-S{0,1} is the sign

-2^(E-bias) is the exponent

-1.F is the significant

So, since we have a finite sets of numbers (or memory), we need our results to be rounded to the next real number as close as possible.

But the distance between two numbers is
> 2^(-nbitsF) · 2^(E-bias) 

so the rounding can really give "far" results, or unexpected (like overflowing or underflowing)

The precision of a machine is defined by the distance from 1 and the nearest floating point number.
As an example, open an Octave shell and execute "0.4*3 == 1.2"
it should return true, right? ;)

---

### Post by WW on 2008-10-29
[What Every Computer Scientist Should Know About Floating-Point Arithmetic](http://docs.sun.com/source/806-3568/ncg_goldberg.html)

---

### Post by ahmatti on 2008-10-30
> **WW said:**
> Matlab shows similar results, if you look more closely:
```

>> x = [5 2 2; 4 31 1]
x =
     5     2     2
     4    31     1
>> x/x
ans =
    1.0000    0.0000
    0.0000    1.0000
>> format long e
>> x/x
ans =
     9.999999999999998e-01     1.907131576043213e-17
     1.118373745381119e-17     1.000000000000000e+00
>>

```

No it doesn't, you just typed in x incorrectly, here's the correct output from Matlab:

```

>> x = [5 2 2; 4 32 1]

x =

     5     2     2
     4    32     1

>> format long e
>> x/x

ans =

     1     0
     0     1


```

---

### Post by WW on 2008-10-30
As ahmatti points out, I used a different x matrix in my earlier post.  I edited the post to show the result with the correct x.

---

