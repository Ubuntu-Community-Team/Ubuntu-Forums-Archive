---
title: "KDE slowness! = O"
date: 2005-09-17
forum: Desktop Environments
---

### Post by Eleaf on 2005-09-17
Ok, I JUST installed kubuntu breezy yesterday.  It all installed fine and is looking great!  However, a day later, kde is taking up %100 of my cpu for about 20 minutes or so after everything has loaded up.  In top it says 0% idle and I can barely even move the mouse.  The entire system suddenly is just completely slow like that.  This wasn't happening before but suddenly when I started today it did this.  This actually happened before when I was running Hoary and wanted to try kde so I apt-get'd it and it worked fine until a little bit later and did this same thing!  That was on another hard drive as well.  And this hard drive I'm using now is new.

In top, there aren't any processes that are using way too much cpu.  It would add up to be like %3 or %4 but my idle percentage is at 0 and the processor is being taken up by the processes to the right of the idle area.  kded is using up about +%40 of my memory however which doesn't sound right.  This is weird and makes my system quite unusable!!!  I've tried updating things and restarting and all that but its doing the same thing.  

This happend to me multiple times before.  Can somebody help?  
I'm running on ppc with 500 mhz and 320 megs of ram.  It blazed before this started happening.

Thank you! :?

---

### Post by Takis on 2005-09-18
I don't suppose by any chance you ran Kaffeine, did you...?

---

### Post by hanover.fiste on 2005-10-13
I'm seeing the same thing. Why do you ask about kaffeine? I'd ran it a day or so ago, but the problem didn't start until after I'd logged out and back in a few times.

---

### Post by Takis on 2005-10-14
Kaffeine (the hoary version, at least) has a known bug where when you try to quit, the window closes but the process goes into an infinite loop, eating all your CPU cycles. If you've been logging out and in, this shouldn't be a problem, though.

As a side note, the memory issue (KDE taking 40% or so) is to be expected, it's a real memory hog.

---

