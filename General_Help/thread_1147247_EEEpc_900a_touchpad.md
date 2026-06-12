---
title: "EEEpc 900a touchpad"
date: 2009-05-03
forum: General Help
---

### Post by balloooza on 2009-05-03
I know what I am talking about, and will do anything the "hard" way.
I have an EEEpc 900a, in hardy the touchpad worked, in jaunty it dosn't.
Simple, I want the old driver, (I was using easypeasy, hardy 8.04, got tiered of using the old version, missing some 8.10 features, but never upgraded untuil now)

Right now it is a 250 paperweight without the touchpad working.

I am foing to be at church, for the entire day, please PM me if you reply, 
Again that is the
EEEpc 900a, and it was working with the 8.04 driver in easy peasy (I guess it is probobly the same as the standered ubuntu 8.04 one.)

I know you will probobly need the out of lspci, but I cannot dp that now.

Thank you for the help.

---

### Post by kamaji792 on 2009-05-16
Not much help for you but I have just installed the Jaunty netbook remix on my 900A and it works fine.

I wonder what version of the Bios you are running?

I am running 703.

All the best

---

### Post by pauna on 2009-05-16
Check your /etc/modprobe.d/options[.conf] or the kernel options in GRUB menu.lst.

I have found that if the file includes "options psmouse elantech=1" as suggested for Hardy, my touchpad does not work at all. If it is empty, my touchpad works so-and-so, but the movement is very jerky. But if I put "options psmouse proto=imps", the touchpad mouse movement is about ok.

I have 901 not 900A, though.

---

### Post by Sato on 2009-06-27
...

---

### Post by Hobgoblin on 2009-07-02
> **Sato said:**
> i have also problems since 9.04 netbook remix with my touchpad of eee 900a. the cursor sometimes "jumps" and is not really accurate.
is there already a solution for this?
thank you in advance :)

Sorry for the delay, I've been trying to fix the same issue for the last couple of weeks.

Try this.

```
gksudo gedit /etc/modprobe.d/options
```
(enter your password)

Then paste the following.

```
options psmouse proto=exps
```

Save the file and reboot.

---

### Post by kamaji792 on 2009-07-15
Actually I have an amendment to make.  My touchpad was not running fine.  Not quite useless but hard to use most of the time.

My solution was to update the BIOS.  I updated to 1001 and now having re-installed UNR (9.04) it works a lot better.  Very occasionally it exhibits the old jumping around habit but it is now a lot better.

I appreciate that BIOS updates are a risky way to go (easy to end up with a fancy paperweight) but it worked for me.

atb

PS - The BIOS updat was done to try and cure problems with the WiFi but had no effect.

---

### Post by t4thfavor on 2009-07-15
I just lick my finger(gross) but it seems to increase the accuracy of the touchpad. It could be just me as I tend to have really dry hands.

But even without my hack it tends to work just fine most of the time.

out of curiosity, how did you update the bios?

---

### Post by Truethanatos on 2009-08-04
Ok has anyone found a solution I have a 900a and I have no touchpad functionality at all not even the mouse buttons I don't know where to start I am quite new to linux and ubuntu I am running the latest jaunty based eeebuntu

Thanks for any help

---

### Post by Legolover64 on 2009-08-04
I am having the same problems with my Gigabyte Tablet Netbook, so any and all help with getting an Elantech touchpad that doesn't work at ALL would be much appreciated!

---

### Post by ed5000 on 2009-08-22
Try this.

```
gksudo gedit /etc/modprobe.d/options
```
(enter your password)

Then paste the following.

```
options psmouse proto=exps
```

Save the file and reboot.[/QUOTE]

* * *


I also have a Asus 900a with netbook remix and the fix by Hobgoblin above (for a jumpy touchpad) works great!  Thanks

---

### Post by bburnaman on 2009-08-30
I experienced the same "jumping" trackpad issue, and the solution posted by hobgoblin works like a charm.

---

### Post by Wired Action on 2009-09-18
Hi, I know this thread is kinda "stale" but I needed THIS (Hobgoblin's post) answer to solve my copy of this exact problem. 
I am using an ASUS EeePC 900A (which I bought specifically BECAUSE it's listed as the most compatible with Ubuntu. 
I am running "eeebuntu" because it seems like it's an unofficial development geared toward this "netbook" hardware. I'm referring to the "kernel tweaks" and specific purpose to develop/retain proper hardware support via, ready to go drivers.

This IS the answer! Please incorporate this solution into Ubuntu Netbook Remix. Just make it standard and then we won't have to type it in every install. I am of the opinion at this time that this solution SOLVES to within a comfortable tolerance this "jumpy cursor" issue in ubuntu on the, specifically, EeePC hardware platform.

*this post is for my vote that this solution WORKS and I can, as of the time of this posting, verify Hobgoblin's posted solution.

---

### Post by highfructose327 on 2009-10-06
Hobgoblin Thanks! I was having the same issue with a eee 900a with 1.5 easypeasy your fix cleared it right up. Thanks again

---

### Post by NTolerance on 2009-11-02
> **ed5000 said:**
> Try this.

```
gksudo gedit /etc/modprobe.d/options
```
(enter your password)

Then paste the following.

```
options psmouse proto=exps
```

Save the file and reboot.



I'd like to add that this fix is still necessary to get smooth response and multitouch working on the 900A running Ubuntu Karmic 9.10.

---

