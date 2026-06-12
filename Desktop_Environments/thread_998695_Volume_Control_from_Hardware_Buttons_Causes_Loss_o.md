---
title: "Volume Control from Hardware Buttons Causes Loss of Menus"
date: 2008-12-01
forum: Desktop Environments
---

### Post by ScarySquirrel on 2008-12-01
__________________________________________________________________________
**Antecedent Actions:**
     1.  I press either of the hardware volume change buttons on the face of my HP zv6000 laptop.
**Symptoms:**
     1.  The Volume Control Widget Popup, which I assume is properly called the Volume Control OSD, keeps respawning and increasing or decreasing the volume repeatedly when I press either of the volume change buttons on my HP zv6000 laptop.  
     2.  When I attempt to resize any window, only a "ghost" outline of the window appears around the window.
     3.  All "right-click" or panel menus fail to appear.
     4.  Those "right-click" menus which apply to specific programs, such as the context menus for VLC Media Player and Firefox, do appear.
__________________________________________________________________________
**Proposed Solutions (Temporary):**
     1.  [tried -> mixed_win] When I press the mute button, the OSD stops spawning until I press the volume increment or decrement buttons again.:arrow: **Concluded the following:** This only affects these specific buttons.
     2.  [tried -> mixed win]  When I restart Ubuntu, the use of my Menus returns. :arrow: **Concluded the following:**  Something which only loads when I press the hardware's increment volume and decrement volume buttons is related to this problem.
     3.  [tried -> ***FAIL***]  Load an older kernel, 2.6.24-21 generic, from the GRUB boot menu.
**Proposed Solutions (Permanent):**
     1.  [***?***]Disable the volume control OSD of Gnome-settings-daemon.
     2.  [tried -> ***FAIL***] Turn off Visual Effects in the menu System/Preferences/Appearance Preferences.  :arrow: **Concluded the following:**  This is a problem with my gnome's interface to my hardware driver, not just with some gnome widget.
     3.  [tried -> ***FAIL***]  Use a live CD with a different Integrated Desktop Environment, such as XFCE.
__________________________________________________________________________
**Links to Related or Similar Threads:**
     1.  [[gnome] Disable Volume Control OSD of Gnome-settings-daemon]("http://ubuntuforums.org/showthread.php?t=816791")
     2.  [Gnome Volume Control Crashes]("http://http://ubuntuforums.org/showthread.php?t=998221&highlight=Volume+Control")[/font]
     3.  [Volume Control Crashes without Root Access]("http://ubuntuforums.org/showthread.php?t=998221&highlight=Volume+Control")

---

### Post by Grunik on 2008-12-02
I can confirm the above post: the same laptop model, and having exactly the same problem with same behaviour.

---

### Post by ScarySquirrel on 2009-02-20
I tried this on Linux Mint XFCE, and I had the same problem.  How do I escape this?  Because the Desktop Environment Software does not seem to matter, this is a kernel problem.
I guess we just have to use an old kernel, but I do not know how to do that.
Could I, perhaps, use a different driver for my Audio Controller?
Someone please help me out on this.  I have waited for three months now.  Does anyone even have an idea of what I could do?
First it's my wireless card, now this.  When does it end?

---

### Post by ScarySquirrel on 2009-02-26
I have gone on the chat rooms and spoken with helpful people, but they seem to have no idea what causes the problem.
Does anyone else have the same model of laptop as I do and have weird problems after upgrades with their volume?

---

### Post by roh112 on 2009-03-04
I have the same problem with hardware's volume control.

On ubuntu 6.10 everything worked fine. But on 7.04+ until the new 8.10, everything keeps failing with volume control. I have the exact same problems on my fujitsu siemens amilo 1420 laptop.

Since i tried different distros and also have the same problem, i assume it is a driver issue. Anyone tried getting rid of pulse audio?

I do hope for a solution, this bug is really bugging me:(

---

### Post by markloser835 on 2009-04-12
Yes, my Compaq R4000 worked fine with 8.04, but with 8.10 I have this same problem. I was hoping LinuxMint 6 (based on Ubuntu 8.10) would resolve the issue, but it has the same problem on my laptop. Anyone found a fix yet???

---

### Post by ScarySquirrel on 2009-05-16
Has anyone submitted a bug report yet?
I don't know if I have a launchpad account.

---

### Post by ScarySquirrel on 2010-04-24
The following depicts the response of the community: 

[IMG]http://icanhascheezburger.files.wordpress.com/2010/04/funny-pictures-cat-does-not-care.jpg[/IMG]

---

### Post by ScarySquirrel on 2010-04-24
> **ScarySquirrel said:**
> Has anyone submitted a bug report yet?
I don't know if I have a launchpad account.

No posts about it. Back then I wanted SOME kind of comments from a non-noob before I entered the bug. Hell, I didn't even know the package name. But now taht I have the chops I guess annoyance is my only excuse. *tries bug report* 
... :-k
Now how to file a bug in the bugreport program? 
...
>.<
I get this strange feeling like I've tried to do this before...

---

### Post by mo79 on 2010-05-01
I have a NEC Versa M500e and I've had this problem on 8.04 and now 10.04 (I didn't jump to non-LTS versions). It's not too much of a show stopper for me as I naturally fiddle with the volume control slider by mouse, but even so it's annoying that that's in there, should I ever unconsciously go for the keys.
As I soon as I press 'Fn' and one of the F keys to lower or raise volume, the volume goes all the way up or down and the graphic for the speaker flickers repeatedly. I can only get rid of it by shutting down.

---

### Post by ragax3r on 2010-06-25
> **mo79 said:**
> I have a NEC Versa M500e and I've had this problem on 8.04 and now 10.04 (I didn't jump to non-LTS versions). It's not too much of a show stopper for me as I naturally fiddle with the volume control slider by mouse, but even so it's annoying that that's in there, should I ever unconsciously go for the keys.
As I soon as I press 'Fn' and one of the F keys to lower or raise volume, the volume goes all the way up or down and the graphic for the speaker flickers repeatedly. I can only get rid of it by shutting down.
I am experiencing the exact same thing. I am used to use my volume buttons to change level but every time I hit FN and F7/F8 my complete PC locks up. I'm on Ubuntu 10.04 and my soundcard is a Realtek ALC662 and my laptop is a Chinese brandless one. I;m hoping to get a fix soon.

Hans

---

