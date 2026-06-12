---
title: "Will older .debs work on newer Ubuntu?"
date: 2008-02-17
forum: Gaming &amp; Leisure
---

### Post by BigSilly on 2008-02-17
Can anyone help with this? I have a couple of .deb files installed on my Gutsy that I am hoping to use on Hardy Herron when that comes out. Specifically, I have an older version of SDLMame (v0.120u1) that I want to stick with for some time if I can, simply because I have a full set of roms that I'm happy with and I like the performance I get. Is it likely that this .deb file will work OK on Hardy, and if not, what should I do to enable it?

Thanks dudes. :)

---

### Post by RemmyLee on 2008-02-17
Debian packages are dependent on certain versions of libraries. There is a good chance that they won't as the binary contained inside the package was linked against those versions.

---

### Post by Vadi on 2008-02-17
Give it a try - sometimes they work, sometimes they complain about libc6.

---

### Post by frenchn00b on 2008-02-17
> **BigSilly said:**
> Can anyone help with this? I have a couple of .deb files installed on my Gutsy that I am hoping to use on Hardy Herron when that comes out. Specifically, I have an older version of SDLMame (v0.120u1) that I want to stick with for some time if I can, simply because I have a full set of roms that I'm happy with and I like the performance I get. Is it likely that this .deb file will work OK on Hardy, and if not, what should I do to enable it?

Thanks dudes. :)

```
less INSTALL ;  ./configure  ; beep ; make ; sudo make install ; beep 
```

---

### Post by BigSilly on 2008-02-18
> **frenchn00b said:**
> ```
less INSTALL ;  ./configure  ; beep ; make ; sudo make install ; beep 
```

Wow. What's that then? 

Thanks for your replies people. :)

---

### Post by frenchn00b on 2008-02-18
> **BigSilly said:**
> Wow. What's that then? 

Thanks for your replies people. :)

that s fun, I'd say. 

It is compiling it, and make sure it will work.

Using non suitable .deb is not DEBIAN way, maybe Ubuntu, and certainly not adviced. You have high risks to break your system.

Compiling from source is great. It can also teach you more about Linux. There things that may be difficult to compile time to time, but 70-90pct is easy to compile when you installed well your box.

---

### Post by BigSilly on 2008-02-18
Thanks for your advice there frenchn00b. I know what you are saying about the Debian way vs the Ubuntu way, but I would love to be able to use this older Mame for a while longer. Hopefully your advice will help me do that safely.

Funny you should mention compiling though. I've just tried to compile the newer version (0.123) on my PCLinuxOS install, just to see how it fares with my roms collection. But as a compiling noob myself, I'm having some difficulty. Typing ./configure had no effect, but when jumping straight to make all seemed to go well. However, when I typed ```
su -c "make install"
``` it says```
 no rule to make target "install". Stop.
``` There doesn't seem to be any errors in the terminal output, and I made sure I had the necessary libraries installed that it needed.

As I say, I'm a complete novice when it comes to compiling, and of course this is an Ubuntu forum. But if you can offer any advice here I'd be most grateful. Many thanks in advance.

---

### Post by frenchn00b on 2008-02-18
> **BigSilly said:**
> Thanks for your advice there frenchn00b. I know what you are saying about the Debian way vs the Ubuntu way, but I would love to be able to use this older Mame for a while longer. Hopefully your advice will help me do that safely.

Funny you should mention compiling though. I've just tried to compile the newer version (0.123) on my PCLinuxOS install, just to see how it fares with my roms collection. But as a compiling noob myself, I'm having some difficulty. Typing ./configure had no effect, but when jumping straight to make all seemed to go well. However, when I typed ```
su -c "make install"
``` it says```
 no rule to make target "install". Stop.
``` There doesn't seem to be any errors in the terminal output, and I made sure I had the necessary libraries installed that it needed.

As I say, I'm a complete novice when it comes to compiling, and of course this is an Ubuntu forum. But if you can offer any advice here I'd be most grateful. Many thanks in advance.

as root

```
#

apt-get build-essential
#

apt-get automake
#

apt-get autoconf
#
apt-get  linux-headers-$(uname -r) 
```

then 

```
sh ./configure
```
make
make install

what gives in that folder :
ls -la ?

---

### Post by Vadi on 2008-02-18
To become root, you do "sudo su", btw. And "exit" to become normal again.

---

### Post by BigSilly on 2008-02-19
Thanks for your help frenchn00b. I got all the programs etc that you recommended, but it still wouldn't work at make install sadly. This is what I get with ls -la:

```
[bigsilly@x1-6-00-0b-6a-7d-54-73 sdlmame0123]$ ls -la
total 32700
drwxrwxr-x 13 bigsilly bigsilly     4096 Feb 18 18:15 ./
drwxrwxr-x  7 bigsilly bigsilly    4096 Feb 18 17:38 ../
drwxrwxr-x  2 bigsilly bigsilly     4096 Jul 22  2006 artwork/
drwxrwxr-x  2 bigsilly bigsilly     4096 Jan 25  2007 cfg/
-rwxr-xr-x  1 bigsilly bigsilly   190592 Feb 18 18:15 chdman*
drwxrwxr-x  2 bigsilly bigsilly     4096 Sep  3  2006 comments/
drwxrwxr-x  2 bigsilly bigsilly     4096 Oct  7  2006 diff/
drwxrwxr-x  2 bigsilly bigsilly    4096 Oct  5 14:59 docs/
drwxrwxr-x  2 bigsilly bigsilly     4096 Jul 22  2006 ini/
-rwxr-xr-x  1 bigsilly bigsilly   10276 Feb 18 18:15 jedutil*
drwxrwxr-x  2 bigsilly bigsilly     4096 Nov 14 20:47 keymaps/
-rw-rw-r--  1 bigsilly bigsilly    12662 Feb  5 13:50 makefile
-rwxr-xr-x  1 bigsilly bigsilly    43924 Feb 18 18:15 makemeta*
-rwxr-xr-x  1 bigsilly bigsilly 31885876 Feb 18 18:15 mame*
drwxrwxr-x  2 bigsilly bigsilly     4096 Jan 29  2007 nvram/
drwxrwxr-x  3 bigsilly bigsilly     4096 Jan 25 13:20 obj/
-rwxr-xr-x  1 bigsilly bigsilly    95960 Feb 18 18:15 regrep*
-rwxr-xr-x  1 bigsilly bigsilly   48484 Feb 18 18:15 romcmp*
drwxrwxr-x  2 bigsilly bigsilly     4096 Jul 22  2006 roms/
-rwxr-xr-x  1 bigsilly bigsilly     4645 Mar  9  2007 runtest*
-rw-rw-r--  1 bigsilly bigsilly    11410 Feb  5 13:45 SDLMAME.txt
drwxrwxr-x  8 bigsilly bigsilly     4096 Feb  5 13:47 src/
-rwxr-xr-x  1 bigsilly bigsilly    28084 Feb 18 18:15 src2html*
-rwxr-xr-x  1 bigsilly bigsilly     7196 Feb 18 18:15 srcclean*
-rwxr-xr-x  1 bigsilly bigsilly    12224 Feb 18 18:15 testkeys*
-rw-rw-r--  1 bigsilly bigsilly   951190 May 21  2006 ui.bdf
-rw-rw-r--  1 bigsilly bigsilly    50574 Feb  5 13:47 whatsnew.txt

```

sh ./configure gave me no such file or directory, and su -c "make install" just said the same as before. I realise this is an Ubuntu forum of course and not a PCLOS hangout, but I'd just like to say thanks to you for assisting me with my first proper compiling of a program. If there's any further advice you could add, you would make me very happy indeed! I'd *love* to know what you do to make this work! :)

---

### Post by pixel :-) on 2008-02-19
i'm not aware of the specific program,but the "./configure" part is sometimes skipped :KS ,in less sophisticated source paqueges.

But you seem to have a makefile :)

Try "make".If it starts compiling for a while thats good.If it runs in errors, try guessing the library you are missing.For finding libraries 
[http://ubuntuforums.org/showthread.php?t=474790&highlight=skype]("http://ubuntuforums.org/showthread.php?t=474790&highlight=skype")
it's good.Are you sure that it finished successfully the compilation,when theirs no "./configure",generally is up to you to investigate the failures of compilation.Also,you have to install the headers of the libraries,generally the paquages "nameOfLibrary-dev",just having the library is not enough.

For installation i recommend installing "checkinstall".You type "checkinstall" instead of "make install",it builds a minimal package."make install" simply copies the files to there designated place in the file hierarchy.

---

### Post by BigSilly on 2008-02-23
Well, I've had absolutely no joy at all here! I re-installed PCLinuxOS today, after having a few days playing around with Mandriva, and decided to try this again.

As I say, ./configure does nothing, but make seems to complete just fine with no reported errors. It's just make install that won't even talk to me! It says "no rule to make target 'install'. stop." and that's it. There's definitely a makefile, and I think it needs editing, but I can't find anything that could possibly explain to me how to go about it. I'm quite happy to spend time compiling software, but it's very frustrating when there's no clear idea of what to do.

Please - I understand many of you compile software regularly, can you help me get a grasp on this? Help before I go nuts!

---

