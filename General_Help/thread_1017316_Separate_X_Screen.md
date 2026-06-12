---
title: "Separate X Screen?"
date: 2008-12-20
forum: General Help
---

### Post by nielscase on 2008-12-20
I have enabled the separate x screen for my dual monitors with my nvidia 9600gt video card, and on my second screen when I rotate my virtual desktops it shows all of it but on screen it cuts off part of it.

I'm not sure if that makes sense but I can't figure out how to fix it.

[[IMG]Regular Desktop (first monitor_[/IMG]](http://img370.imageshack.us/my.php?image=regularfe2.png)
[[IMG]Cutoff Desktop (extended monitor)[/IMG]](http://img370.imageshack.us/my.php?image=52916022aw7.png)

The extended one is a different resolution that the Regular one, but it seems that the extended one is conforming to the regular one.

---

### Post by earthpigg on 2008-12-21
im not sure i understand the exact description of your problem, but yes it is awkward using two monitors at once with different resolutions.

---

### Post by howefield on 2008-12-21
In nvidia-settings, have you got the resolution set to auto ? if you have try setting it to the correct resolution and save.

Is the problem occuring only when you rotate the screens ?

---

### Post by nielscase on 2008-12-21
> **howefield said:**
> In nvidia-settings, have you got the resolution set to auto ? if you have try setting it to the correct resolution and save.

I tried that and it didn't change anything.

> **howefield said:**
> Is the problem occuring only when you rotate the screens ?

Nope when I rotate the screen with the cube effect I can see the whole desktop.  Then when I choose a desktop it has the black space over it again.  I can move my mouse on to the black area in the picture and use it I just cant see what is there.

---

### Post by nielscase on 2008-12-21
No one knows?

---

### Post by Ng Oon-Ee on 2008-12-21
> **nielscase said:**
> No one knows?
I've had this some times. Normally goes away when I mess around a bit with xorg.conf. Never was quite able to figure out why it happened, though. I'm currently not using Xinerama, so that may be your root cause, try disabling it. Though what you get is separate screens instead of a big desktop, then.

---

### Post by Harbard on 2008-12-22
I have similar situation.  One monitor is 1280x1024 and the other is 1680x1050.

I do not use Xinerama or Twinview.  I never got either to work "correctly".  I used the "NVIDIA X Server Setting" tool.  Resolution is set to auto for both screens and seperate X screens for each. 

FIRST BACKUP xorg.conf
FIRST BACKUP xorg.conf
FIRST BACKUP xorg.conf


The other caveat, is run the "NVIDIA X Server Setting" as root.

Open a terminal.
Type "sudo su"
enter your password.
type "nvidia-settings"
make your changes and save them.
reboot.

You did "FIRST BACKUP xorg.conf" right??

---

