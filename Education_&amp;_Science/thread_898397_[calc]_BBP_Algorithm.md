---
title: "[calc] BBP Algorithm"
date: 2008-08-23
forum: Education &amp; Science
---

### Post by Pyro.699 on 2008-08-23
Hello,

From my understanding the [BBP algorithm]("http://mathworld.wolfram.com/BBP-TypeFormula.html") can extract individual hexadecimal values from the numerical constant pi. I went through the arduous task of calculating out 5 sets of the formula:
[IMG]http://mathworld.wolfram.com/images/equations/BBP-TypeFormula/Inline7.gif[/IMG]

and here are the results i got:

3.13333333333
0.00808913308913
0.000164923924115
0.00000506722085386
0.000000187892900938
0.00000000776775121518
0.000000000344793293051
0.0000000000160918771555
0.0000000000007795702954
0.0000000000000388711525991

Now i don't really see how i can get 3.1415926 from those numbers, unless you add them all together (which i guess is why there is a sigma sign there (duh -.-)) but i thought that the formula was used to extract individual digits without requiring the preceding ones. Basically i did what the sigma implied, first k = 0 which gave me 3.133; then k = 1 which gave me 0.00808; and so on. Ive been doing research for the past 2 weeks and still i am unable to yield the proper formula.

Thanks
~Cody Woolaver

---

### Post by hubie on 2008-08-23
I think what you want to do is described very nicely [here]("http://en.literateprograms.org/Pi_with_the_BBP_formula_(Python)").

---

### Post by Pyro.699 on 2008-08-23
Thank you,

There seems to be some error in that formula. If you read closely you notice that the accuracy of the script diminishes over time. That script calculates a range of hexadecimal digits. Is it not possible to just type in 1, and receive the first place digit(1); type in 2 and receive the second place digit(4)?

Thanks again
~Cody Woolaver

---

### Post by hubie on 2008-08-24
> **Pyro.699 said:**
> Is it not possible to just type in 1, and receive the first place digit(1); type in 2 and receive the second place digit(4)?

Strictly speaking, no.  The first rub to the algorithm is that it gives you the hexadecimal digits.  If you wanted to know the decimal digits then you'd need to convert the hex digits, which means you need to know all the digits that came before it (in other words, you need to calculate all the previous digits, thus defeating the purpose of using the algorithm in the first place).

If you use the algorithm (especially as implemented in the previous link), then you can input a number n and you'll get out the nth hex digit.  What is spat out is the nth digit plus the digits that follow.  The accuracy of the digits that follow depend on the level of precision used.  The first set of algorithms uses floating point arithmetic and the resulting precision depends on rounding errors (the author posits that it should be good to calculate out to the billionth digit or so).  The author also presents integer arithmetic code that supposedly gives you a set level of precision.  What also looks interesting is he presents a nice routine if you want to just sequentially generate the digits.

---

