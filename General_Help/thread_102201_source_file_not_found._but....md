---
title: "source file not found. but..."
date: 2005-12-11
forum: General Help
---

### Post by ophir on 2005-12-11
Hello everybody,
my first post here :) 

I'm new to linux, and when I did use it I ued Fedora.
I recentally installed ubuntu and it seems nice.

I'm trying to install my wireless network card using ndiswrapper.
when I try to compile using 'sudo make' I get the following error:
Can't find kernel sources in /lib/modules/2.6.12-10-386/build;
  give the path to kernel sources with KSRC=<path> argument to make

I read in this forum how to run a command that obtains the source from the internet. and I unpacked it from tar to that directory. now the directory contains what I think is the kernel source (but how can I really know?).

why do I still get the error while trying to complie?

10x

---

### Post by ophir on 2005-12-11
can anyone please help? at least read??

---

### Post by zoiks on 2005-12-11
Use apt-get or Synaptic to install the sources.  The package is called something like "linux-source-x.x.x" where x.x.x is the kernel version you are running.

---

### Post by ophir on 2005-12-11
I did use apt-get (as I saw on a message in this forum).
it downloaded the tar file to /usr/src
after extracting it it still didn't work. even if while running make ip point to the location using KSRC it still gives that error message.

what am I doing wrong?

---

### Post by zoiks on 2005-12-12
[QUOTE=ophir]I did use apt-get (as I saw on a message in this forum).
it downloaded the tar file to /usr/src
after extracting it it still didn't work. even if while running make ip point to the location using KSRC it still gives that error message.

what am I doing wrong?[/QUOTE]

OK so I don't know much about these things, but in the past when I've had to compile modules I've had to go to the root of the kernel source directory and perform commands like "make cloneconfig" and "make prepare-all".  I don't know what these do exactly, but they did the trick for me.  (Note I didn't compile the whole kernel, this was just to prepare the source configs or soemthing or other so that I could compile modules.)

Otherwise, I might suggest an exact listing of what your commands are, along with the associated output from the command prompt.  It might make it easier for readers to understand the situation.

---

