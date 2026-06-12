---
title: "Multimedia problems on Jaunty"
date: 2009-04-27
forum: General Help
---

### Post by bbahar on 2009-04-27
Hello,
I've just installed the Jaunty from scratch and I must admit, it is an amazing product . However, there are few things that making problems, I wonder if I can get any help.
(1) Listening to music or see movie is problematic.
(2) Installed VLC and Amarok. Mp3 files play only in Rythmbox 
    and VLC. Amarok doesn't react. What can it be..?
(3) I am not able to see any media format at all. I've tried  
    Mplayer, VLC but with no success. It opens the file and after 
    a second it shuts the application. It's a bit annoying.
(4) I installed the necessary codecs,(ubuntu-restricted-extras). 
    Before that I tried all the pulse alternatives but no results.

Please help..

Baruch

---

### Post by nandemonai on 2009-04-27
Check out medibuntu.
[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by bbahar on 2009-04-27
Hmmm,thanks for quick reply. 

I ran the mplayer thru command line, got this error message :

X11 error: BadAlloc (insufficient resources for operation)

But when I type mplayer -vo x11 file.avi it works.. 

It's same with VLC too...

Any suggestions ..?

---

### Post by mb_webguy on 2009-04-27
Did you add the Medibuntu repository to your software sources and install the ubuntu-restricted-extras, non-free-codecs, and libdvdcss2 packages?

---

### Post by 65_volks on 2009-04-27
I'm having the same problem on my system.  I installed the ubuntu-restricted-extras, non-free-codecs, and libdvdcss2 packages

---

### Post by habana on 2009-04-27
Check out this Howto - it works for me.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by 65_volks on 2009-04-27
> **habana said:**
> Check out this Howto - it works for me.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Longest Howto ever! Changed so much stuff and was no help. Still having same issue.

---

