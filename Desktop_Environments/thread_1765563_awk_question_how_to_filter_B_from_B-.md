---
title: "awk question: how to filter B from B-?"
date: 2011-05-23
forum: Desktop Environments
---

### Post by dmikulec on 2011-05-23
I want to filter data that has been ranked as A+, A, A-, B+, etc. I want to find items that have rank B or better. I'm finding that awk does not recognize the + or the -; so, I have to filter for < C and manually remove data ranked as B-. I've tried assigning "B+" < B  and B < "B-" without success. Any thoughts on how to assign the hierarchy to correctly rank the data?

---

### Post by areeda on 2011-05-23
You could do it with a regular expression (invented by the devil to make our lives difficult until we learn the syntax).

How about something like:
```

awk  '{if ($1 ~ /(A[+-]*|B[^-]|B$)/) print;}'  <file>

```I tested it with the following and it seems to work:
```

A John
A+ Mark
A- Mary
B Sue
B- Fred
B+ Lisa
A+ Kathy
B- Sam
C+ Bob
C Dave
C- Jim

```Joe

---

### Post by dmikulec on 2011-05-27
Areeda,

Thanks for your reply. Sorry for not responding sooner but I needed time to try your suggestion. I'm struggling with the devil - and learning the differences between text- and regex-directed engines.

Your approach is so straightforward compared to mine; now I'm wondering what's wrong with my neurons. I'm still having troubles with my syntax, though, in recognizing B- and suspect the "-" character may be some other encoding. But, I've proven that I can write syntax that recognizes B+, so that's a big improvement. Thanks again for your help. 

Don

---

### Post by areeda on 2011-05-27
Don,

Regular expressions tend to be obscure, arcane and hard to debug (not to mention all the adjectives I use in private).  If they weren't so powerful and concise no one would use them.

Notice in my expression above the [^-]  that stands for any character except a -. You could also use [+]* which stands for 0 or more +'s (you may need \+ since plus can mean one or more in some situations)

Why not show us your regex.  Perhaps we can help.

Joe

---

### Post by dmikulec on 2011-05-29
Areeda,

Thanks for another response and your kind offer to continue with this problem. I'm using $3 ~ /(B[^\-]|A[+-]?)/ which is returning data with a rating of B+ or better, not B or better. If I use /(B[^\-]|B|A[+-]?)/, awk returns everything better than B- (as does /(B|A[+-]?)/ ). I've set FS = " " but this hasn't changed the result. I've tried many other combinations including /(B[+]|^(B[-])|A[+-]?)/ which returns the B+'s and B-'s but not the B's along with all the A's. Curiously, when the order is reversed /A[+-]?|B[^\-]?)/, awk returns only A's, no B's at all. I'm stumped.

Don

---

### Post by areeda on 2011-05-29
> **dmikulec said:**
> Areeda,

Thanks for another response and your kind offer to continue with this problem. I'm using $3 ~ /(B[^\-]|A[+-]?)/ which is returning data with a rating of B+ or better, not B or better. If I use /(B[^\-]|B|A[+-]?)/, awk returns everything better than B- (as does /(B|A[+-]?)/ ). I've set FS = " " but this hasn't changed the result. I've tried many other combinations including /(B[+]|^(B[-])|A[+-]?)/ which returns the B+'s and B-'s but not the B's along with all the A's. Curiously, when the order is reversed /A[+-]?|B[^\-]?)/, awk returns only A's, no B's at all. I'm stumped.

Don
You're welcome Don, this is kind of fun for me.

I see the problem and it might be easier to fix it that to explain it so if you can post some (made up ) test data, I'll take a shot.

Here's an attempt to explain:

if $3 can contain only the grade and it's either one or 2 characters try:
/(B[^-]|B$|A[+-]?)/

The $ after the B says the string ends with B.

Joe

---

### Post by dmikulec on 2011-05-30
Areeda,

Much thanks. Your suggestion works. I never would have thought to use $ as I understood that to mean "at end of line", not "at end of string".

Don

---

