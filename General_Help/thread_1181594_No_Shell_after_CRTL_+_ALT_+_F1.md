---
title: "No Shell after CRTL + ALT + F1"
date: 2009-06-08
forum: General Help
---

### Post by damien_d on 2009-06-08
Hello,

I am attempting to drop back to a shell to install a beta version of the nvidia drivers.

The classic way to do it is to CTRL+ALT+F1, then login, kill gdm and voila!

However, after the CTRL-ALT-F1 step, the screen has a single flashing cursor in the top-left corner - no login prompt and no hint that shell is alive.  This is repeatable across reboots, as well as other virtual consoles ( ... + F2 etc)

Has anyone come across this sort of issue before?  

I am running Ubuntu 9.04 x86_64.  I can happily provide details as necessary.

  -- Damien.

---

### Post by keplerspeed on 2009-06-08
Hey Brisbanite (assuming the same Brisbane.. unless Brisbane CA?)! I am running 9.04 x86_64, nvidia card (9400GT).

Does the gui function fine within the normal ctrl-alt-f7 console (the one you log into normally)??

Can you enter anything into this fashing cursor virtual console?

Is this repeatable via live cd?

---

### Post by sonofusion82 on 2009-06-08
i had some problems with my ati drivers too, totally unable to go to shell ctrl-alt-f1.
the only way i could access my machine is via SSH, once I am in, i reset my xorg.conf and luckly that fixed my video woes...

---

### Post by damien_d on 2009-06-09
> **keplerspeed said:**
> Hey Brisbanite (assuming the same Brisbane.. unless Brisbane CA?)! I am running 9.04 x86_64, nvidia card (9400GT).


Yep.  Go the maroons!  Similar setup, have have a 8600GT, a 8400GS and nForce 750A (I like multiple monitors) :)

> **keplerspeed said:**
> 
Does the gui function fine within the normal ctrl-alt-f7 console (the one you log into normally)??


Yes, I have perfectly normal desktop GUI (gnome) operations

> **keplerspeed said:**
> 
Can you enter anything into this fashing cursor virtual console?


If I press enter, it looks like it does a carriage return (sometimes!), but not other characters respond.

> **keplerspeed said:**
> 
Is this repeatable via live cd?


Haven't yet tried.  In the end I ssh'd into it from another machine, killed gdm and installed the drivers that way.

  -- Damien

---

### Post by damien_d on 2009-06-09
> **sonofusion82 said:**
> i had some problems with my ati drivers too, totally unable to go to shell ctrl-alt-f1.
the only way i could access my machine is via SSH, once I am in, i reset my xorg.conf and luckly that fixed my video woes...

This is the approach I took too. Did you discover the root cause?

---

### Post by damien_d on 2009-06-09
Just did a little more testing:

CTRL+ALT+F1 = blanking cursor
CTRL+ALT+F7 = back to X

F1 through to F6 all display the same symptom.

When in the "terminal" the screen does NOT respond to any key-presses (not even "enter" as reported earlier.

---

### Post by lightstream on 2009-06-09
I suppose you get the same blinking cursor if you switch to a TTY from the command line with the following:
```
sudo chvt 1
```
Also have you left it at the blinking cursor for a while, to see if you eventually get any timeout errors?

---

### Post by ushimitsudoki on 2009-06-09
I had this problem, and this is how I fixed it:
[http://meandubuntu.wordpress.com/2009/06/09/fixing-missing-virtual-terminal/](http://meandubuntu.wordpress.com/2009/06/09/fixing-missing-virtual-terminal/)

Give it a look, maybe?

---

### Post by damien_d on 2009-06-09
> **lightstream said:**
> I suppose you get the same blinking cursor if you switch to a TTY from the command line with the following:
```
sudo chvt 1
```
Also have you left it at the blinking cursor for a while, to see if you eventually get any timeout errors?

Yes, I get the same blinking cursor.   I just left it for a couple of minutes, then switched back using ctrl-alt-f7

---

### Post by damien_d on 2009-06-09
> **ushimitsudoki said:**
> I had this problem, and this is how I fixed it:
[http://meandubuntu.wordpress.com/2009/06/09/fixing-missing-virtual-terminal/](http://meandubuntu.wordpress.com/2009/06/09/fixing-missing-virtual-terminal/)

Give it a look, maybe?

Wow.... bit of a workaround!  I'm currently getting GLX sorted again after my nvidia-185 experiment (it broke, but that's another thread).

For the moment, I've just been ssh'ing in.   Not a great workaround, but it's simple and easy.

  -- Damien

---

### Post by ushimitsudoki on 2009-06-09
Well, if you only care to reboot, you can use the [magic sysreq sequence]("http://kember.net/articles/231/reisub-the-gentle-linux-restart"):

ALT + SysReq + R/E/I/S/U/B

---

