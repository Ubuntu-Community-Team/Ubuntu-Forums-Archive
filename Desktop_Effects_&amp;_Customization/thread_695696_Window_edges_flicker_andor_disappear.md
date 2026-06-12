---
title: "Window edges flicker and/or disappear"
date: 2008-02-13
forum: Desktop Effects &amp; Customization
---

### Post by camini on 2008-02-13
My emerald themed window borders are flickering and sometimes disappearing since a couple of days.

This seems to be for active window only.

Clicking another window brings back the window edges.

What has changed on my system lately:
- latest kernel update (2 days ago)
- latest nVidia driver (using envy) (one week ago - did not notice problem after update)


Anyone else suffering from this?

---

### Post by camini on 2008-02-13
Actually, this only happens with the FireFox window version 2.0.0.12.

---

### Post by camini on 2008-02-13
And only when on the Google home page..  weird!

---

### Post by andre.klaver on 2008-02-14
I've got the same problem with Mozilla Firefox 2.0.0.12 as well. I've done the same upgrades as you did (what a coincidence) The odd thing is it is site-depended. 

This page will give the flickering with my setup for sure:
[http://teletekst.nos.nl/?101-01](http://teletekst.nos.nl/?101-01)

But...loading another page from here by following a link doesn't give the flickering. It is not necessarily the same page giving this error (even stranger). Very odd. firefox will give the flickering even when a 'faulty' page is loaded in another tab.  Very hard to reproduce...

---

### Post by DiscoWay on 2008-02-14
I am also experiencing this problem.  That is interesting that it is only happening in firefox.  Hope someone figures it out. It's kinda annoying.

---

### Post by andre.klaver on 2008-02-15
Mozilla Thunderbird has it too...I just noticed that today. Compose a new mail window has the same problem.

---

### Post by andre.klaver on 2008-02-15
I think I know what causes it. 

If there is a field on a webpage to input tekst (e.g. the field to enter a search item in Google) and you've placed the cursor there it start doing that when hovering over buttons. 

It is not necessarily Firefox who has this. Openoffice has the same problem on my setup. The flickering is as periodic as the cursor is blinking.  Slow it down or make it faster in the keyboard settings in your system menu and you will see what happens. If I disable the blinking cursor the flickering bar will not appear...

---

### Post by andre.klaver on 2008-02-17
Anyone for a solution?!

---

### Post by camini on 2008-02-18
aha - good catch!  I noticed this weekend it wasn't only for google page indeed.

Just for my info, what 'window edge theme' are you using?  I'm using dark glass emerald theme.

---

### Post by andre.klaver on 2008-02-18
Hi! I'm using 72934-Mac OS X Aero theme. 

It doesn't really matter which one you use. As soon as there are animated buttons, the window edges will flicker...

---

### Post by andre.klaver on 2008-02-20
No one with a solution? Maybe some other thread?

---

### Post by tommohawk on 2008-02-20
I have the same sort of problem.

Check out these two threads over at compiz forums and nvnews.  You may be able to try some of the suggested fixes there.  Didn't quite work for me but it is definitely due to the recent driver updates.

[http://forum.compiz-fusion.org/showthread.php?t=7066](http://forum.compiz-fusion.org/showthread.php?t=7066)

[http://www.nvnews.net/vbulletin/showthread.php?t=104822](http://www.nvnews.net/vbulletin/showthread.php?t=104822)

---

### Post by tommohawk on 2008-02-20
> **andre.klaver said:**
> I've got the same problem with Mozilla Firefox 2.0.0.12 as well. I've done the same upgrades as you did (what a coincidence) The odd thing is it is site-depended. 

This page will give the flickering with my setup for sure:
[http://teletekst.nos.nl/?101-01](http://teletekst.nos.nl/?101-01)

But...loading another page from here by following a link doesn't give the flickering. It is not necessarily the same page giving this error (even stranger). Very odd. firefox will give the flickering even when a 'faulty' page is loaded in another tab.  Very hard to reproduce...

Just to point out that this does not appear to be a fault with Firefox in particular because I have managed to reproduce it in others.  

The easiest way to reproduce this fault is to have lets say Firefox open.  You do not have to be on Google, the fault occurs on any website where you have a text entry box.  Simply put your mouse over the text entry box and click in it.  Once you have the blinking cursor then move your mouse to the window control buttons, you will see the artifacts/graphic corruption appear.

You can even put the cursor in the url entry box and then move the mouse and it happens (at least it does on my system)

There is more information over at the compiz forums as per my previous post but to be honest I haven't managed to fix it yet.  Best fix is to downgrade to the previous nvidia drivers but then you may have other issues (like the black screen bug or the system freezing except for the mouse pointer bug).

Interesting to know how people get on.......

---

### Post by HDave on 2008-02-21
I have this problem when running Emerald on Compiz.  It happens on any window for me.  I am using a theme that pulses the color of the buttons.

It didn't start happening to me until I upgraded the kernel on my Gutsy to 2.6.24-7.

What kernel are you guys using and are you also running emerald?

---

### Post by tommohawk on 2008-02-21
> **HDave said:**
> I have this problem when running Emerald on Compiz.  It happens on any window for me.  I am using a theme that pulses the color of the buttons.

It didn't start happening to me until I upgraded the kernel on my Gutsy to 2.6.24-7.

What kernel are you guys using and are you also running emerald?

Hmm interesting, must admit I haven't tried disabling emerald but might do that now and post back later.  My kernel is 2.6.22-14-generic on an i686 platform.


Update:  removed emerald - problem still exists!  It's definitely a compiz issue in relation to the latest nvidia drivers.

---

### Post by andre.klaver on 2008-02-22
Looking at those other threads posted here it seems to be an NVIDIA issue. I don't feel much like reverting to an older driver as some mention in those threads. 

The Kernel I use compiz/emerald with is 2.6.22-14-generic and the NVIDIA driver version is NVIDIA UNIX x86 Kernel Module  169.09  Fri Jan 11 14:38:28 PST 2008.

---

### Post by mgmiller on 2008-02-22
Try this:
open the Emerald Theme Manager 
go to the  Edit Themes tab 
go to the Buttons tab 
and  uncheck the "Use Button Halo/Glow for inactive Windows" check box.

You can leave it off, or sometimes, just toggling it off and on was enough.

This fixed a number of weird blinking cursor type things for me.

---

### Post by tommohawk on 2008-02-23
Still no real solution to this problem but I do have the following progress...

I have just upgraded my kernel to the current Hardy development 2.6.24-generic and used the Hardy repos to update my system including the nvidia driver.  Strangely enough everything is now working like a dream..........

So far there has been no graphics corruption, titlebar problems, black screen flashes or system hangs.

Like I said.... so far......

Now, a word of warning, it worked for me but there is no guarantee it will work for you.  To upgrade your kernel you must add the Hardy main repository and I would initially advise you to only upgrade the packages that are essential, namely the kernel packages and the nvidia packages.  If you do more that is up to you but be warned you will be using a development release.

I upgraded about 1,300 packages and my system appears to be stable, well probably more stable than it was with the gutsy packages anyway!

---

### Post by andre.klaver on 2008-02-27
I was going to upgrade to hardy heron in April anyhow so I will just sit this one out...see what happens then...

---

### Post by andre.klaver on 2008-05-25
I did a fresh install of Ubuntu 8.04 and it was gone...untill I used Envy to upgrade my NVIDIA Display drivers to version 169. Must be, as I noticed before, a driver issue. I hope some NVIDIA upgrade in the future will solve this some day...

---

