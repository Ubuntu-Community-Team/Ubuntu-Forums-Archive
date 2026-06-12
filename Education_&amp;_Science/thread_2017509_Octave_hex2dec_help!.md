---
title: "Octave hex2dec help!"
date: 2012-07-05
forum: Education &amp; Science
---

### Post by nrg85 on 2012-07-05
Hi,

I need some help regarding the hex2dec() function in Octave.
I've a column vector with single characters and if I pass it to the hex2dec() it parses as it would be a row vector. 
For example: 
```
i = ["a"; "b"; 'c']; hex2dec(i)
```results in:
```
ans =  2748
```however if the array contains more characters per row it parses it correctly:
```
i = ["0a"; "0b"; '0c']; hex2dec(i)
```resulting in:
```
ans =

   10
   11
   12
```The question is, is it possible to force the hex2dec() function to parse a column vector as a matrix?

Many thanks in advance!

---

