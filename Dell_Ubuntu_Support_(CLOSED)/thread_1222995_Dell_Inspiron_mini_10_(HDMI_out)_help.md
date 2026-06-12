---
title: "Dell Inspiron mini 10 (HDMI out) help"
date: 2009-07-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kobii on 2009-07-25
I recently purchased a Dell Inspiron Mini 10, and I threw in the extra couple of bucks for the hdmi adapter. From the looks of it the command would be Fn-F1 that has the laptop display/monitor symbol on it. It does nothing when hooked to an hdmi TV. I've tested the HDMI connection on the TV and it works fine for DVD/Blu-ray from a different source. And the Function keys work with the other config options(battery display, brightness, not so much sound control(but I do have sound, just can't control it via Fn keys). Pressing Ctrl or Alt or Shift seems to have the same functions as Fn(F?).

The specs of the laptop are:

Inspiron Mini 10
Inspiron 1010, Intel Atom Processor Z530, 1.6GHz, 533MHzFSB, 512K L2 Cache
Z530 (1.6GHZ) Atom, 1GB RAM
10.1 Inch High Definition Widescreen Display (1366x768)
Intel Graphics Media Accelerator 500

plus some other stuff that would make this post really long.

Anyways, is there any way via command prompt or otherwise to test the HDMI Port to see if it is even recognized? Any drivers that might be available for it? Anything that might help to get it working?

---

### Post by kobii on 2009-07-27
I updated the driver for the Intel GMA Poulsbo(something or other)

Now the netbook screen has a name "LGD 10" instead of the generic name.

Through the monitor settings it detects a connection to the TV(although it says the TV is a 36 inch instead of a 42 inch.

While screwing around trying to get the TV to display properly I saw the Ubuntu Desktop on the TV for a fraction of a second, I was only able to do this once. 

One of the errors I got said something about auto-configuring my virtual resolution and then asking me to log off which didn't seem to accomplish anything.

---

### Post by andersja on 2009-07-31
Sounds like a possible bug. 

Try reporting by opening a command line or pressing Alt+F2, then typing: 
ubuntu-bug xserver-xorg-video-intel

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) (see in particular: Writing a useful report
> 
When a developer fixes a bug, they will test that the bug occurs, make a small change to the program, then see if the bug has gone away. Depending on the bug, they might need to run the same test dozens or hundreds of times. When you submit a bug report, it's important to specify three things:

   1. What you expected to happen
   2. What actually happened
   3. The minimal series of steps necessary to make it happen, where step 1 is "start the program" 

Fill in the description field with as much information as you can, including the release of Ubuntu you are using and steps for someone else to recreate the bug. It is better to have too much information in the description than not enough.

Only describe a single problem per bug report so that each can be followed up on in detail. If you experience several issues file separate reports. 

---

### Post by K4KEP on 2009-08-11
I just got a Mini 10 and need to hook it up to a VGA monitor. Has anyone found a inexpensive interface. All I am hearing is $200+. Dell told me the HDMI connector had both digital and analog available on that connector but LOCAL Computer Direct Outlet say they can not find any analog on it. Dell won't discuss it further. (8.04)

---

