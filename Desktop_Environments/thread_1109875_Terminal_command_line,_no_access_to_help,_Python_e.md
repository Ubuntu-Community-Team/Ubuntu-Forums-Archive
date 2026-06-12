---
title: "Terminal command line, no access to help, Python etc"
date: 2009-03-29
forum: Desktop Environments
---

### Post by Rob_Riethmuller on 2009-03-29
Hi All
Firstly I'm new to Linux- Ubuntu 8.4.1

Terminal does not recognise commmands like Help, Python, etc 
e.g.
rob@rob-Linux:~$ Python
bash: Python: command not found

At one stage I could reboot the computer and and it would work only the first time I had the terminal window open.
However this seems to have ceased. I had reinstalled Terminal and Python to no avail


Please help. What am I missing?
Cheers
Rob Riethmuller

I am attempting to convert from VB6 to Python, using Ububtu 8.04.1  - Python 2.5
Being experienced with VB6, Python code has many similiarities
so this does not present any particular problem HOWEVER getting past the first post???

Now when terminal was working and would recognize "Python', then to run a simple program. Just bombs out

This is the simple program below Saved as Mary.py (From a tutorial)
in the following directory
/home/rob/Python/Python Programs (Do I need to point to this directory?)
If so, then could you please show the code.
-------------------------------------------------
#! /usr/bin python

print "Mary had a little lamb,"
print "it's fleece was white as snow;"
print "and everywhere that Mary went, "
print "her lamb was sure to go."
---------------------------------------------------
I type in at the Terminal command line
>>> Python Mary.py

The result is

  File "<stdin>", Line 1
    Python Mary.py
              ^
SyntaxError: invalid syntax 

Please help. What am I missing?
Cheers
Rob Riethmuller

My Computer: Intel(R) Pentium(R) 4 CPU 1.70GHZ
		512 MEG RAM  39 GiB disk available
		Working on a seperate partition Win XP Home

---

### Post by lloyd_b on 2009-03-29
Uh - "python", not "Python".  Linux is case sensitive...

Lloyd B.

---

### Post by Rob_Riethmuller on 2009-03-30
Hi

Lloyd, thanks for the quick reply.
Yes the lower case 'python' does the trick
Cheers
Rob R

---

