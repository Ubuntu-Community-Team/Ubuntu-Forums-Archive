---
title: "Guidance About Shell Scripting."
date: 2010-05-20
forum: Education &amp; Science
---

### Post by Peon666 on 2010-05-20
Hi!
 
To start with, I'm a student of Telecommunications Engineering and I'm new to Ubuntu. My summer vacations are stating next week and I don't have much to do during them, so I was considering to try my hand on Linux Shell Scripting during these vacations. 
 
So, I need some guidence regarding the following:
 
1- What is the actual purpose behind Shell Scipting?
2- Where should I start from? (other than guidance, any link etc. in this regard would be appreciated)
 
Thanks.

---

### Post by nateperson on 2010-05-20
I use simple shell scripts to automate tasks that I would otherwise do from a bash terminal...  Say, I have a perl script that calls 18 other different things, that takes 2 hours to run, and i need to run it 12 times one with different options each time... but its not worth editing the perl script, so i end up with:
```
#!/bin/bash
perl myScript.pl optionA

....

perl myScript.pl optionL
```
And it takes care of it till the next day.  Plus a bunch of other assorted simple tasks...


Here's a link to look at:[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html")

---

### Post by Peon666 on 2010-05-20
Thanks for the reply.
 
Okay, I guy suggested me to do csh. What's the difference between csh and bash? What's more preferable?

---

### Post by Peon666 on 2010-05-20
This might also be helpful: I've done C/C++ at university, so what form of shell scripting would be most compatible with it?

---

### Post by memilanuk on 2010-05-20
bash, or something like it, seems to be the default on many Linux versions.  There are other options to suit nearly any taste, though.

This might be of help:

[http://en.wikipedia.org/wiki/Unix_shell](http://en.wikipedia.org/wiki/Unix_shell)

---

### Post by anglican on 2010-05-21
> **Peon666 said:**
> Thanks for the reply.
 
Okay, I guy suggested me to do csh. What's the difference between csh and bash? What's more preferable?
Dont use csh, use bash. [Here's]("http://www.faqs.org/faqs/unix-faq/shell/csh-whynot/") why.

H

---

