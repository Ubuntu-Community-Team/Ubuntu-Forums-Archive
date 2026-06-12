---
title: "Font problem converting real to char in matlab/octave"
date: 2010-10-04
forum: Education &amp; Science
---

### Post by Glenn Jones on 2010-10-04
Hey all,

I'm having some slight issues with octave/matlab when I attempt to cat a string and a variable. It's probably easier to show an example

t=1
a=['abcbd',t]
a = abcd

or

char(t)
ans=

If you cann't see  its a square with |00|
                                       |01|

The issue appear to be when you convert a real variable to a character.

This error is true in both octave and matlab. Has anyone else experience this. Does anyone have any suggestions as to how to solve this problem?

Cheers

It appears that the issue is with the unicode display. Apparently the system default is not the same as used in octave and matlab hence the issue. Still no closer to solving the problem

---

