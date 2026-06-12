---
title: "Gnome C compiler and Ghostscript installation"
date: 2006-02-05
forum: Desktop Environments
---

### Post by benmoreassynt on 2006-02-05
Hi,

I'm in the process of installing Ghostscript 8.15.1.

As part of this process I needed to install gcc Gnome C compiler. Having done that, when I run the Ghostscript installer I get the report:


> C compiler cannot create executables

Looking at the log file reveals the following, which seems to be the problem ...

> /usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:1704: $? = 1
configure: failed program was:
| #line 1677 "configure"
| /* confdefs.h. */
... snip ...
configure:1743: error: C compiler cannot create executables

Can anybody tell me what is missing and what I need to install to get this to work? I have not been able to find what crt1.o relates to.

Many thanks in advance.

Ben

---

### Post by benmoreassynt on 2006-02-05
I've since discovered that crt1.o is part of glibc, the Gnu C library, which cannot be installed by apt-get or synaptic package manager as far as I can see. 

Can anybody tell me anything about this, if there is an easy way to install glibc, or another way to get around this problem.

---

### Post by taurus on 2006-02-05
Try

sudo apt-get install build-essential

---

### Post by benmoreassynt on 2006-02-06
Thanks again, that did the trick (albeit the ghostscript installation crashed at a later stage!)

---

### Post by taurus on 2006-02-06
Do you really have to have ghostscript?  You can use other similar programs in repo too...

---

### Post by benmoreassynt on 2006-02-06
[QUOTE=taurus]Do you really have to have ghostscript?  You can use other similar programs in repo too...[/QUOTE]

What I actually need is the version of ps2ascii that Ghostscript 8.15.1 contains. I have Ghostscripts 7.?.? and ps2ascii already, but the versions that come with Ubuntu do not do what I want them to do (namely take OCRed text from PDF files and save them to text files). They seem to be oldish versions.

From work on another computer I know that ps2ascii in 8.15.1 will work for my needs. I suppose I could install it some other way if I knew which version of ps2ascii I needed to use.

There are other ways and means of doing this (namely using Windows), but I have a script that takes the text out, concatenates it, and inserts it into a database all in one go, which would definitely be advantageous.

Thanks for again your advice.

---

### Post by kaamos on 2006-02-06
Have you tried installing the "binutils" package? That contais the ld executable.

---

### Post by benmoreassynt on 2006-02-06
Taurus,

You got me thinking straight at last.

I can use pdftotext instead of ps2ascii, which works perfectly without needing to mess around more with Ghostscript.

Thanks

Ben

---

### Post by taurus on 2006-02-06
[QUOTE=benmoreassynt]Taurus,

You got me thinking straight at last.

I can use pdftotext instead of ps2ascii, which works perfectly without needing to mess around more with Ghostscript.

Thanks

Ben[/QUOTE]
Glad to hear that you've found something that actually works now without pulling your hair out over compiling...  :cool:

---

