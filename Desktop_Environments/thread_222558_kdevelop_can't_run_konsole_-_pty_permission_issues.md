---
title: "kdevelop can't run konsole - pty permission issues"
date: 2006-07-25
forum: Desktop Environments
---

### Post by smylie on 2006-07-25
Hi

I'm trying to run kdevelop w/ konsole (straight out of synaptic).
Kdevelop works without error, but when I click on the konsole tab, it complains that: 

"Konsole is unable to open a PTY (pseudo teletype). It is likely that this is due to an incorrect configuration of the PTY devices. Konsole needs to have read/write access to the PTY devices."

In the terminal i get the following:

kdevelop3: WARNING: Unable to open a pseudo teletype!
Uh oh.. can't get terminal attributes..

In /dev/pts i have only two pts, both owned by me w/ read/write permissions set. 

It's definitely a permissions issue though, as if I run kdevelop as root, konsole works fine.

Any one know what I could be doing wrong?

Cheers
Dave Smylie

---

### Post by smylie on 2006-07-26
just in addition - i can run konsole by itself with no problems ...

---

### Post by smylie on 2006-08-01
*bump*

---

### Post by smylie on 2006-08-06
*nudge*

---

### Post by smylie on 2006-08-12
*tap*

---

### Post by smylie on 2006-08-18
*tickle*

---

### Post by fdoving on 2006-08-19
Check that the shell kdevelop/konsole tries to load exists.
It's a confusing error message, you get this message if you set the default shell for a user to something that doesn't exist, and try to run konsole.

Just my 0.2$

- Frode

---

### Post by smylie on 2006-08-24
> **fdoving said:**
> Check that the shell kdevelop/konsole tries to load exists.
It's a confusing error message, you get this message if you set the default shell for a user to something that doesn't exist, and try to run konsole.

- Frode

Thanks for the input - I'd assume it's just running the default shell from the user entry in /etc/passwd? Is this not the case?

---

