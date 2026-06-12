---
title: "ATI dual screen on natty 11.04"
date: 2011-06-08
forum: Desktop Environments
---

### Post by BFG on 2011-06-08
Running classic desktop, with ATI Catalyst ccc with 2x 1680x1050 screens, I can't get the behaviour I am used to in 9.10.  I used to use "Big desktop".

The closest seems to be "Multi-display desktop with display(s) 2".  I like that now when I get a video to go full screen, it picks one screen instead of spread badly across both.  

But I have these problems:

1.
I use VirtualBox 4.0.8 installed from the VB repo.
I've been able to run XP clients and resize them across the dual displays to get one massive virtual machine. Very useful for what I do for business. Essential in fact.

Now in 11.04, I am restricted to a small window. If I try and resize the guest window, it lets me drag it out as large as possible, but when I release the mouse the guest window resizes to 1680 wide. I can't set it larger. 


2.
Minor problem.  Big desktop lets me have one desktop background across both monitors. Not possible now.


I tried Single Display Desktop (Multi-desktop)
- results in two distinct separate desktops.  Can;t move items between. And there is a Xinemara option which is hopeful - but activating this completely borked X, needing recovery mode to uninstall ccc before I could log in again.

---

### Post by BFG on 2011-06-23
Bug raised with Virtualbox:

[http://www.virtualbox.org/ticket/9102#preview](http://www.virtualbox.org/ticket/9102#preview)

---

