---
title: "Please put prefix when posting new thread."
date: 2014-02-27
forum: Forum Feedback &amp; Help
---

### Post by ventrical on 2014-02-27
Hi All,

 I have a KVM network switcher with various flavours of Ubuntu. I like to be helpful as possible but it would be more expeidient for me if persons where to choose  a prefix before they entered a new post. It creates a lot of downtime sifting through un-prefixed threads. 

 Thanks 

 Ventrical

---

### Post by TheFu on 2014-02-27
I don't set a prefix because my system isn't listed.  Let me explain.
* Ubuntu Server installed.
* fwvm and/or LXDE installed, then all the added stuff I won't want gets purged - like nano, network manager, lots of gnome stuff, leafpad, lxterm*, and whatever tracking packages happen to get installed.

So - which system should I select from the prefix choices?

I'm of the strong opinion that providing solutions using CLI is the best way to solve problems, not spending 5x the number of words to explain point-n--click stuff that will change in 6 months with a new GUI is released.  Many of the solutions I used in 1995 still work - and I have scripts from that period that are still used daily.

Which is better is debated here constantly.

---

### Post by ventrical on 2014-02-27
> **TheFu said:**
> I don't set a prefix because my system isn't listed.  Let me explain.
* Ubuntu Server installed.
* fwvm and/or LXDE installed, then all the added stuff I won't want gets purged - like nano, network manager, lots of gnome stuff, leafpad, lxterm*, and whatever tracking packages happen to get installed.

So - which system should I select from the prefix choices?



That would be:

[other]

 I use fvwm-crystal also. Razorqt too + xmonad .. but .. to simplify it, if I do an original Ubuntu install and then stack another desktop on top of it I would still choose [ubuntu]. At least that gives mods, devs , guests and noobs a general idea  of a starting point to emulate the bug or employ a fix. Putting nothing can be misleading in U+1. A person may have originally installed Xubuntu and then installed unity-desktop and have a crash, post a new thread and use the header [ubuntu]. This is the wrong header. It should be [xubuntu]. At least thats the way I see it. It would help others to keep their ducks in a row. Using CLI since 1995, I would think you would know better.

Regards..

---

### Post by Elfy on 2014-02-27
*Thread moved to **Forum Feedback & Help**.*

---

### Post by ventrical on 2014-02-27
I put note in my tagline:)

---

### Post by TheFu on 2014-02-27
[other] - seems so ... so ... foreign. I'm not running OSX or BSD or Arch.

It is mostly Ubuntu-ish, since I only run LTS releases (so I won't be posting to U+1), avoid using untrusted PPAs and really, really, really avoid installing anything from a .deb file.

Other is still correct according to the admins?

---

### Post by ventrical on 2014-02-27
> **TheFu said:**
> [other] - seems so ... so ... foreign. I'm not running OSX or BSD or Arch.

It is mostly Ubuntu-ish, since I only run LTS releases (so I won't be posting to U+1), avoid using untrusted PPAs and really, really, really avoid installing anything from a .deb file.

Other is still correct according to the admins?


Really , it doesn't matter to me.   I thought it would be prudent to mention as a courtesy towards others who may have dups or similar bugs - then -  that user would not have to sift through all those posts only to find out that it was not the same flavour .etc..

Regards..

---

### Post by Hazzabin on 2014-02-27
I agree with ventrical, 
as for example I've seen a supposed fix or idea how to, only to find later that
it was NOT the (lets call it) flavor whatever Ubuntu that I have/using

my opinion only :)

---

### Post by Doug S on 2014-03-01
Seems to me that there should be a [Server] prefix available.

---

### Post by Elfy on 2014-03-01
There is :p

---

### Post by cariboo on 2014-03-01
> **Doug S said:**
> Seems to me that there should be a [Server] prefix available.

There is a Server Platforms sub-forum, we assume if you post there, you are posting about a server.

---

### Post by Doug S on 2014-03-01
> **Elfy said:**
> There is :pSorry. I couldn't see it before.
I was going to post to Ubuntu+1 because my issue was with the trusty daily. Anyway, and luckily just before actually posting, I figured out the issue is my problem.

---

### Post by Elfy on 2014-03-01
> **Doug S said:**
> Sorry. I couldn't see it before.
I was going to post to Ubuntu+1 because my issue was with the trusty daily. Anyway, and luckily just before actually posting, I figured out the issue is my problem.

There wasn't then ...  ;)

---

### Post by TheFu on 2014-03-01
> **cariboo907 said:**
> There is a Server Platforms sub-forum, we assume if you post there, you are posting about a server.

I do post to the server or virtualization forums, when those are relevant.

Where should a post on audio issues on a box with NO Ubuntu-based GUI at all?  The audio devices disappear and reappear after a reboot then disappear again. This is according to **aplay -l**.  Sure, it is "server", but ... none of the GUI solutions that tend to be offered are useful.  I think it is a bad driver or failing hardware - can't tell yet. It all started after a recent kernel update. Not asking for help here, just pointing out that there are always exceptions when only the "distro" prefix is used.  We are ALL DIFFERENT from most computer users after all, just by running Linux.

When I try to help with answers, avoiding the different GUIs is my preference. Much easier to ask them to open a terminal and run commands to get the answers - copy/pasted here  - and not waste bandwidth with images. Asking for the output from **sudo parted -l** is much easier than asking for a very large image of a gparted screenshot so the details can be seen.

Of course, I'm probably in the 0,5% minority.

---

