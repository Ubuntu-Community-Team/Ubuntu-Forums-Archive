---
title: "Moving median, signal processing"
date: 2007-06-17
forum: Education &amp; Science
---

### Post by Richard_L on 2007-06-17
First an example with moving mean.  If the output signal is the mean of current input value and the two values before we write:
y[n] = 1/3( x[n] + x[n - 1] + x[n - 2])
Then we can get the impulse response:
h[n] = 1/3(delta[n] + delta[n - 1] + delta[n - 2] ) 

If the output signal is the median of current input value and the two before we write:
y[n] =  median (x[n] , x[n - 1], x[n - 2])
Is there a way to express this more mathematical?
I want the impulse response h[n].

//Richard

---

### Post by makhand on 2007-06-17
If I remember my dsp correctly, an impulse response is associated with a linear system. A median filter is non-linear, therefore, there isn't an explicit impulse response. 

by writing something like:
y[n] = median (x[n] , x[n - 1], x[n - 2])

you are implying that x[n], x[n-1], x[n-2] are sorted and the middle value is taken. 

Can anyone else confirm my memory?

---

### Post by euler_fan on 2007-06-18
> **makhand said:**
> If I remember my dsp correctly, an impulse response is associated with a linear system. A median filter is non-linear, therefore, there isn't an explicit impulse response. 

by writing something like:
y[n] = median (x[n] , x[n - 1], x[n - 2])

you are implying that x[n], x[n-1], x[n-2] are sorted and the middle value is taken. 

Can anyone else confirm my memory?

Speaking as a statistician (having only the most rudimentary understanding of signals processing) you are essentially correct. In a naive sense the median is the middle number in a sorted list.

More formally, if each frequency is associated with the number of times is observed and divide each of these by the total number of observations(p_i(x)), then the median is the number such that \sum_{i=n-2}^{i=m} {p_i(x)}=.5 and \sum_{i=m}^{i=n}=.5 simultaneously. (sorry if my TeX is a little off).

I can't speak to the impulse response issue. I can say that in the case of three (random?) values it will be impossible to find any better way to express the median. You may try specifying a set A_n where x_i in A_n if i in {i-j|j=1,2,3} and state median(A_n) as opposed to your notation. Not sure if that will save you time anywhere else, though, and ergo whether or not it is worth your effort.

Hopefully that helps.

---

### Post by gargar934 on 2007-06-22
makhand is right on target. An impulse response describes a linear system, which requires the principles of homogeneity(scaling) and superposition hold.

To test for linearity:
given: y[n] = h[n]*x[n]    where * denotes convolution and h[n] is our filter

a system is linear iff:
(Ax[n] + B x[n])*h[n] = Ay[n] + By[n]  where A and B are constants.

It is clear to see that this does not hold for a median filter, and thus there is no way to describe it with an impulse response.

---

