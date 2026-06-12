---
title: "fsck prevents boot"
date: 2008-03-25
forum: Dell  Ubuntu Support
---

### Post by teogearloose on 2008-03-25
The boot sequence on my Inspiron 1420 running Ubuntu 7.10 includes the operation

"fsck 1.40.2"

which provokes a message to the effect that

"os_part" has been mounted 28 times and now check is forced, whereupon a counter works its way up to 15.8%, and hangs. Control-Alt-Delete leads to a repeat.

How can I bypass the forced check?

---

### Post by codeslicer on 2008-03-25
Bypassing fsck is impossible I think. Are you sure that waiting some more time won't finish it? Perhaps it's just checking still but not reporting it to the screen.

Try booting in recovery mode. Later you could install AutoFsck from [http://ubuntuforums.org/showthread.php?t=295262]("http://ubuntuforums.org/showthread.php?t=295262").

---

### Post by teogearloose on 2008-03-25
>>Perhaps it's just checking still but not reporting it to the screen.

That was it!  All I had to do was wait 20 min, and it came out of its stupor.

---

### Post by fragos on 2008-03-26
My disapoint isn't with fsck.  It's with the fact that Ubuntu no longer displays the fact that fsck is running and what the progress is.  Without this and staring at a black blank screen the 1420n feels like it crashed.

---

### Post by davidpbrown on 2008-03-29
An optout was requested on the brainstorm site and appears to be resolved in Heron
[http://brainstorm.ubuntu.com/idea/11/](http://brainstorm.ubuntu.com/idea/11/)

It suggests you will be able to press Esc to cancel the disk check, which is good.

Hopefully it will also be more obvious it's running without being hidden beyond the bottom line of the screen.

---

### Post by lynchman on 2008-04-18
Does anyone know why fsck takes so long on the 1420n?  It takes about 30mins for mine to run, and it always decides to do it at the most inconvenient times.  I have a pure debian server at home w/ about 1tb of storage and running fsck on all of those drives only takes about 10 minutes, and those are old eide drives, not sata....

---

### Post by fragos on 2008-04-18
I noticed the same thing compared to my desktop. I've been thinking about putting Ubuntu in a smaller partition like it is on my desktop. My guess is the smaller partition will fsck faster.  The 1420n disk is 5400RPM and my desktop 7200RPM so that may also be a factor.

---

### Post by lynchman on 2008-04-19
I dunno - I got the 7200 drive - It's slow too.

Maybe it is just something w/ the HD.  The only other thing I really notice that is slow is when saving the state of a virtual machine in VMWare (pretty HD intense operation it seems).  On my desktop it is fast, but on this, it takes a few minutes to save/load a suspended virtual machine.  I usually find it faster to just shut the VM down and restart it each time, which kinda sucks but I'm living with it.

---

### Post by fragos on 2008-04-19
Prior to 7.10 when fsck ran the screen would change to a full size terminal. Not attractive but there was an ASCII character progress bar and some sign of activity. That doesn't happen anymore and the only activity indicator is the disk LED. Very poor human engineering. The 1st couple of times I thought the machine had crashed. There should at the least be a blinking messages and more ideally a progress bar of some flavor. The frequency of running fsck is configurable but running it is for our own benefit.

---

### Post by gbrainin on 2008-04-20
I'm running 7.10 on my 530n, and when it fsck's I still get the full-screen terminal with the ASCII progress bar.

I wonder if the difference in fsck time has anything to do with the filesystem being used.

---

### Post by fragos on 2008-04-20
> **gbrainin said:**
> I'm running 7.10 on my 530n, and when it fsck's I still get the full-screen terminal with the ASCII progress bar.

I wonder if the difference in fsck time has anything to do with the filesystem being used.

Interesting question. Ubuntu by default uses EXT3 and has for some time.

---

### Post by gbrainin on 2008-04-20
> **fragos said:**
> Interesting question. Ubuntu by default uses EXT3 and has for some time.

The other system that the OP was comparing this to is a "pure Debian server," so I thought it might be using a different filesystem.  I'm not sure why that would make that much of a difference, just trying to explore all possible differences.

---

