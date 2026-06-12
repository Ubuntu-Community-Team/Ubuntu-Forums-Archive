---
title: "What apps to use to compile code???"
date: 2009-09-17
forum: Desktop Environments
---

### Post by Silvernail on 2009-09-17
I have Jaunty on one machine and Hardy on the other.

What apps should I down load and install to compile some of the code I find such as kernel 2.6.31?

---

### Post by Shazaam on 2009-09-17
Normally build-essential helps you get started. There is a thread in the sub-forum Tutorials and Tips that deals with compiling kernels. You will probably need to search for it.

---

### Post by Silvernail on 2009-09-17
> **Shazaam said:**
> Normally build-essential helps you get started. 

'build-essential' is a file/directory/tutorial that will give/tell me what/which tools I need to install? Where do I find this?

> 
There is a thread in the sub-forum Tutorials and Tips that deals with compiling kernels. You will probably need to search for it.
This I can do.

Thanks
Dave

---

### Post by theZoid on 2009-09-17
sudo apt-get install build-essential

---

### Post by Silvernail on 2009-09-18
> **theZoid said:**
> sudo apt-get install build-essential

What could be simpler?  It appears I already have those.

What ever it was that prompted me to ask about compiling code has completely slipped my mind. Even though I have the tools, I don't know what to do with them.

Its been 25 or more years since I wrote or compiled code. Back in the days of 8 bit CPUs and 4000 byte Memory.

Things have advance too far for me to catch up. I think I shall sit back and continue to be a user until I can no longer see the screen.

Thanks for the reply.
Dave

---

### Post by Chronon on 2009-09-18
Well, the number of languages in use today has grown, as have the size and complexity of programs that we run on our machines.  This doesn't mean that it's out of reach for you to compile your own software.  Recall that building from source doesn't require that you actually know how to program or understand the language.  (That's only required if you need to make changes to the program.)

Most source code has an accompanying README file that should give you instructions on how to build it.  Often this includes running some configuration script to check that you have the right compilers installed and to generate an appropriate makefile.  Then you can just run "make" in the directory containing the Makefile.  Often the software can then be installed by doing "sudo make install".

Don't let a bit of rust discourage you.  :)

I'm sure after building a few things successfully you'll feel much more confident.

---

### Post by Silvernail on 2009-09-20
If I have 'build essentials' that means I have all the necessary compilers and assemblers?

---

