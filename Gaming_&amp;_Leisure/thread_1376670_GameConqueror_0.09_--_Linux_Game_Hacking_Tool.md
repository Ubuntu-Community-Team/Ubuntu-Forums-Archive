---
title: "GameConqueror 0.09 -- Linux Game Hacking Tool"
date: 2010-01-09
forum: Gaming &amp; Leisure
---

### Post by coolwanglu on 2010-01-09
If you are a game hacker
If you've been looking for a `CheatEngine for Linux`

You can't miss this.

==============================================

GameConqueror is a game hacking tool for linux, it's written in PyGTK and uses scanmem as its backend.

It's supposed to be with most useful features of CheatEngine for Linux.

Currently, I've implemented almost everything about scanning, involving variant data types and scan types:

Data Types: int{8/16/32/64}, float{32/64}, unknown type(int or float) and unknown width(will try each of them), byte array and string
Scan Types: equal, greater, less, changed, unchanged, increased(by), decreased(by)

This should be enough for most cases, so I decided to release it at the current status.

=============================================

Here's how you can get it

PPA (for Ubuntu users)
[https://launchpad.net/~coolwanglu/+archive/scanmem](https://launchpad.net/~coolwanglu/+archive/scanmem)
(I've not test it in 32bit environments or Jaunty, do please inform me if it doesn't work)

SVN
svn checkout [http://scanmem.googlecode.com/svn/trunk/](http://scanmem.googlecode.com/svn/trunk/) scanmem

Homepage:
[http://code.google.com/p/scanmem/](http://code.google.com/p/scanmem/)
make sure you selected the correct version `0.09`

You'll need python and python-gtk to run it, and to build it from source code, you'll need libreadline (this should have been installed for most of you)

=============================================

NOTE THAT GAMECONQUEROR MAY CRASH YOUR PROGRAM DUE TO BUGS OR IMPROPERLY USAGE, DO BACKUP YOUR PROGRESS BEFOREHAND.

To use it, actually I've created a menu item, which could be found in the 'Games' category, or you can run it by executing `gameconqueror`, and please do this in a terminal (see below)

Read the tooltip of the label 'Value' to get familiar with the syntax

About the annoying terminal window, now this is the only place where you can see the progress of scanning, and the error message if something goes wrong. This terrible thing is basically because I've mainly focused on the features of scanmem so far, and I'll fix this in the next version.

=============================================

What will be added in the next (or maybe future) version:

- better ui (progress bar, error message, user interaction, etc...)
- search for pointers
- optional float rounding method
- memory viewer/editor


and what will not be added
- speed hack (I've no idea about how to implement this in Linux, can anyone tell me plz?)
- disassembler
- many other `too powerful` features in CheatEngine


any feedbacks will be appreciated.

---

### Post by coolwanglu on 2010-01-09
Screenshot
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=143038&d=1263059539[/IMG]

---

### Post by Clopin on 2010-01-09
Starting to look very good!
Good job mate (:

---

### Post by stanks on 2010-05-15
I try it with settlers 4 under wine and it works, but there is one problem. when i start to search let's say value for wood (1st time it was stone and 2nd time wood) without reset value program freezes. i had to kill it.

---

### Post by coolwanglu on 2010-05-15
> **stanks said:**
> I try it with settlers 4 under wine and it works, but there is one problem. when i start to search let's say value for wood (1st time it was stone and 2nd time wood) without reset value program freezes. i had to kill it.

yes, that was a known issue, I'll fix it asap

sorry for the trouble

---

### Post by stanks on 2010-05-15
How + and - works? I tried with + but nothing changes.
Will you add something like saving table entries?
For some reason gameconqueror stops updating the values in table (i notice this when i add 2nd value for something).

thanks

---

### Post by coolwanglu on 2010-05-16
> **stanks said:**
> How + and - works? I tried with + but nothing changes.
Will you add something like saving table entries?
For some reason gameconqueror stops updating the values in table (i notice this when i add 2nd value for something).

thanks

The bug should have been fixed in v0.11, please have a check.

'+' means 'increased since last time', this is useful when, for example, there's a hp bar from which you cannot tell the real value.

---

### Post by coolwanglu on 2010-05-17
> **stanks said:**
> How + and - works? I tried with + but nothing changes.
Will you add something like saving table entries?
For some reason gameconqueror stops updating the values in table (i notice this when i add 2nd value for something).

thanks

Oh, if you meant the symbol to the left of 'lock', that thing has not been implemented

---

