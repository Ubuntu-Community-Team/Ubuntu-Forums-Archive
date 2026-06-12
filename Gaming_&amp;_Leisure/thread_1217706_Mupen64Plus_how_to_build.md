---
title: "Mupen64Plus: how to build?"
date: 2009-07-19
forum: Gaming &amp; Leisure
---

### Post by SPARTAN-118 on 2009-07-19
Hi, I was looking for a good N64 emulator for Linux, and I stumbled across thegreenblob's [post on how to install the original Mupen64]("http://ubuntuforums.org/showthread.php?t=464165&highlight=mupen64") running a script he made.

However, he also referred in an edit that to Mupen64Plus, since the original Mupen64 hasn't been updated since 2005. 

Since I have never had any experience in building a program from source code/shell script, could somebody (with more experience, obviously) help me?

SPARTAN-118

---

### Post by Grishka on 2009-07-19
you don't have to compile, they provide the binaries.

---

### Post by SPARTAN-118 on 2009-07-19
See, I don't even know the difference, much less know what to do with those binaries.

What, exactly, am I supposed to do to make Mupen64Plus? 

Enter Terminal commands such as "make dir" "make"?

Please tell me *exactly* what to enter in the Terminal.

Thank you, 
SPARTAN-118

---

### Post by BoyOfDestiny on 2009-07-19
> **SPARTAN-118 said:**
> See, I don't even know the difference, much less know what to do with those binaries.

What, exactly, am I supposed to do to make Mupen64Plus? 

Enter Terminal commands such as "make dir" "make"?

Please tell me *exactly* what to enter in the Terminal.

Thank you, 
SPARTAN-118

Well, I personally compile out of habit. But, binaries, are precompiled executibles (think .exe's). You run them.

As for building it, it's a breeze once you've done it once (that is install what you need to build.) It's been too long so I don't remember which in particular mupen64plus needs. For sure
```
sudo apt-get install build-essential
```

Then after extracting try make.

But, if you aren't really into it, just grab the binaries here
[http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/)

Cheers!

---

### Post by DEagleson on 2009-07-20
I dont know how to build it but i know how to make it work.

Download the binary pack for your version, either 32-bits or 64-bits.
Then extract the folder, and open terminal.
Type "cd (Path to folder)" and press enter.
Type "Sudo ./install.sh" and press enter.
Now it should show up in your games menu.

---

### Post by BigSilly on 2009-07-20
Your best bet could be downloading a .deb [from a PPA]("https://launchpad.net/~fabricesp/+archive/ppa/+build/969248"). There's a 64 bit version [here]("https://launchpad.net/~bojo42/+archive/ppa/+build/946075"). I'm using the 64 bit package from bojo42 myself.

Hope this helps.

---

### Post by SPARTAN-118 on 2009-07-20
> **DEagleson said:**
> I dont know how to build it but i know how to make it work.

Download the binary pack for your version, either 32-bits or 64-bits.
Then extract the folder, and open terminal.
Type "cd (Path to folder)" and press enter.
Type "Sudo ./install.sh" and press enter.
Now it should show up in your games menu.

**_EDIT**_: Your method worked, I was just having trouble with the "cd" (change directory) command; I kept forgetting to add the / in front of home.

Aside from the question of making me permanent root, I have other questions:

will all the plugins I installed (according to the README) still work, or did it just install the binaries?

Also, did running ```
$ sudo ./install.sh
``` install all the other directories in the "Mupen64Plus-1-5-bin-32" folder (ie the roms subdirectory)?

Because isn't the file "mupen64plus.v64" a plugin? or, wait, *is* that a test rom?

**_Original post**_: Ya, see, I tried following the directions in the README, however, for some reason, I can't use the command "su" (super user) to become root. When I try to enter my password for sudo, it just uses my password as a command.

I will try your method of installing, but I need to know something for the future:

how do I make myself root/administrator?

I am the only user on this computer, and I'm not sure how to change it so Terminal commands are always root. Like I said, I'm the only user on here, so I'm not worried about security.

SPARTAN-118

---

### Post by BoyOfDestiny on 2009-07-22
To answer that last bit,

```
sudo su
```
Will give you root in terminal
I prefer using sudo instead, just before the command you need to run with root privilege...
As for forgetting the /, instead of /home/user, you can just type
```
~
```

It's pretty simple, to cd to let's say your desktop
cd ~/Desktop
This time saver won't work a with a root session though (since it will just take you to root's home.) 

I would suggest not getting in the habit of being root unless you have a string of commands that would require typing sudo a lot...

---

### Post by SPARTAN-118 on 2009-07-23
> **BoyOfDestiny said:**
> 
I would suggest not getting in the habit of being root unless you have a string of commands that would require typing sudo a lot...

Most commands I type in Terminal require sudo, such as ```
$ sudo apt-get install
```

Also, BoyOfDestiny, I'm not that familiar with make, so could you please tell me how you compile source code? Mupen64Plus is quite slow for me, so I want to see if I can build Project 64 (a Windows emulator) on Ubuntu.

SPARTAN-118

---

