---
title: "float point arithmetic"
date: 2009-03-22
forum: Education &amp; Science
---

### Post by flylehe on 2009-03-22
Hi,
I learned from someone's C++ code something I believed to be about float point arithmetic. However I am not familiar with this subject.

Here we are trying to multiply two small numbers, add products of many pairs of such small numbers and take logarithm. For example, to compute log{sum_{i from 1 to N)} x_i * y_i}.

He claimed that:

1. multiplying two small numbers x_i and y_i directly results in less accuracy in precision, so it is better to first take natural logarithm of each number, then sum them up and then take exponential back, i.e. x_i * y_i = exp[log(x_i) + log(y_i)];

2. instead of adding many such products together straightforward, he first calculate max_{i from 1 to N} (log(x_i) + log(y_i)), let's say log_max, then log{sum_{i from 1 to N} exp[log(x_i) + log(y_i) - log_max]} + log_max.

I was wondering if these tricks can actually increase the accuracy compared to straight forward computation and why? If possible, could you please point me to some sources that could enlighten me a little more on how to dea with issues of such kind?

Thanks a lot!

---

### Post by euler_fan on 2009-03-25
> **flylehe said:**
> 
1. multiplying two small numbers x_i and y_i directly results in less accuracy in precision, so it is better to first take natural logarithm of each number, then sum them up and then take exponential back, i.e. x_i * y_i = exp[log(x_i) + log(y_i)];

2. instead of adding many such products together straightforward, he first calculate max_{i from 1 to N} (log(x_i) + log(y_i)), let's say log_max, then log{sum_{i from 1 to N} exp[log(x_i) + log(y_i) - log_max]} + log_max.


There's precision and there's accuracy. The thing to worry about in this context is precision and on that front addition is vastly better than multiplication. The reason is a combination of error propagation and over/underflow.

As for error propagation, recall that while many numbers can be written nicely in a finite number of binary digits, many of your small ones can't. Ergo they are approximated with an error term p, as x(1+p). If you multiply lots of number together, you end up with a net error term of (1+p)^n and this can get out of hand rather quickly if you're not careful and there is a rather low level of precision (float is much more susceptible than long for instance). Consequently, by changing the problem into one of summing logs, we can keep the error term in the form of n(1+p) which is much nicer.

As for the second, if you stick with regular small numbers (even ones like 0.1) and multiply enough of them together you get numbers smaller than your data type can handle and this is bad for self-evident reasons.

The second trick isn't making any sense to me because I can't see how to algebraically reduce it to a simple product. I posit, however, you are trying to show us a centering scheme designed to have most of the work be done on numbers of `reasonable' scale which is always a good thing in this area.

For better (or at least a more in depth answer) consult a Numerical Analysis textbook.

---

