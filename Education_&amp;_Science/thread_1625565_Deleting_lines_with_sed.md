---
title: "Deleting lines with sed"
date: 2010-11-19
forum: Education &amp; Science
---

### Post by lorenz_b on 2010-11-19
Hi all,

I have a couple of .pdb files (plain text) and I want to get rid of the lines that end with: [11xspace]H[2xspace].

see below for two example lines:

ATOM  27253  C1  DUM M   1      26.914  -4.292 -53.865  1.00 20.00           C  
ATOM  27254  H3  DUM M   1      27.892  -4.099 -54.221  1.00 20.00           H  

There are solutions around, but I would like to do that with sed.
Can anyone help me?

cheers,
Lorenz

---

### Post by DaithiF on 2010-11-19
if the exact count of space chars (11 before, 2 after) is important, then:
```
sed '/ \{11\}H  $/d'
```or if the amount of whitespace doesn't matter (as long as there is some), then:
```
sed '/ \+H \+$/d'
```

---

### Post by lorenz_b on 2010-11-19
Thank you very much.

I'd propably go with your 2nd solution (I was looking through the files and observed that the spaces before the H may also be less than 11).

Does your solution provide the safety that the "spaces-H-spaces" expression is only recognize when located at the end of the line? There may be H's also somewhere in the middle of a line, but those lines should not be deleted (except there is a "spaces-H-spaces" at the end again).

best,
Lorenz

---

### Post by DaithiF on 2010-11-19
> **lorenz_b said:**
> 
Does your solution provide the safety that the "spaces-H-spaces" expression is only recognize when located at the end of the line? 

Yes, the '$' anchors the pattern to the end of a line.

---

