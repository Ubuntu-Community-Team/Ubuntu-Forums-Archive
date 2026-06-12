---
title: "How to install parsec in ubuntu."
date: 2009-05-29
forum: General Help
---

### Post by ankurkhurana on 2009-05-29
I am using ubuntu 8.04 and need to install [glomosim]("http://pcl.cs.ucla.edu/projects/glomosim/").But to install that i first need to install [parsec.]("http://pcl.cs.ucla.edu/projects/parsec/")i am a newbie and i am experiencing problem.Does redhat platform based installation will work for ubuntu .Also if it does pleaseexplain how to do it.it will be very helpful.Thank you.also can you tell me how to set environment variables

---

### Post by boyz.226 on 2009-10-29
@ankurkhurana


Please look up on [this ]("http://rupeshkushwaha.blogspot.com/2009/10/glomosim-with-ubuntu.html")link

---

### Post by ebinephrem on 2012-11-23
[FONT=Arial,Helvetica][FONT=Arial,Helvetica][COLOR=#000000][SIZE=4][COLOR=#6666FF]**How do I install Parsec?**[/COLOR][/SIZE] Unzip the distribution.  It should create a directory called 'parsec-dist'. Within parsec-dist, there are directories for a variety of operating systems and compilers.  (Some unofficially supported operating systems are included in the old-os subdirectory.) 
  On unix, move (i.e. rename) the correct directory for your operating system to /usr/local/parsec. 
  On windows, move (i.e. rename) the correct directory to C:\Parsec 
  Please note: the eventual directory structure should be (using a windows example):
C:\Parsec\bin
C:\Parsec\include
C:\Parsec\runtime
etc.  It should **not** be c:\parsec\windowsnt-4.0-vc6\* 
  If, for some reason, you can't install parsec in the correct directory, you can still use it, by setting the environment variable PCC_DIRECTORY to where you *did* put the directory. 
[/COLOR][/FONT][/FONT]

---

### Post by coffeecat on 2012-11-23
Old thread - closed.

---

