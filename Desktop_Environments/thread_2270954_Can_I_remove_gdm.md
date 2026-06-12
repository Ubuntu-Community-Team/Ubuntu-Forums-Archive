---
title: "Can I remove gdm?"
date: 2015-03-26
forum: Desktop Environments
---

### Post by mickee384 on 2015-03-26
While troubleshooting my video driver issue, I inadvertently installed gdm. I believe the command I was trying to run required it. Forgetting 2 things, 1. the power of the terminal and 2. that terminal will do pretty much anything you ask for, (Not knowing the outcome - should have signaled me to stop. But alas, I did not.) I have lightdm and I think the gdm may be conflicting as I get occasional computer freezes. So was wondering if I can just remove gdm?

---

### Post by grahammechanical on 2015-03-26
We cannot run LightDM (Display Manager) and Gnome Display Manger (GDM) at the same time. One or the other has to be in use with the other not used. So, if we have LightDM installed as well as GDM installed then we can remove the one we do not want. But make sure that you are loading with LightDM before you remove GDM.

Regards

---

### Post by slickymaster on 2015-03-26
There are no drawbacks and no risks in removing gdm. But as grahammechanical stated, be sure you are under a LightDM session when running```
sudo apt-get remove gdm
```

---

### Post by mickee384 on 2015-03-26
Thanks for the help. How do I know for sure I am in lightdm?

---

### Post by mickee384 on 2015-03-26
When I first installed gdm, it asked me to choose the default. It was pre-selected as lightdm, but the keyboard wouldn't work and mouse wouldn't as I was in the alt F1 screen, so did a power down. Booted up looking like I expected, so I am pretty sure I am using the lightdm.

---

### Post by deadflowr on 2015-03-26
> **mickee384 said:**
> When I first installed gdm, it asked me to choose the default. It was pre-selected as lightdm, but the keyboard wouldn't work and mouse wouldn't as I was in the alt F1 screen, so did a power down. Booted up looking like I expected, so I am pretty sure I am using the lightdm.

Is the login screen the same as before?
(With the username and password box off to the left a little and not centered in the screen.)

If the login box is off to the left like UBuntu's normal login screen, then you are running lightdm.

That's the unity-greeter, and for what I remember, there is no version of that that will work with gdm.
So gdm would have a generic login screen, so to speak.

But..
to switch back and forth from one to another run,
```
sudo dpkg-reconfigure lightdm
```
select which one you want and reboot.
(I think you can simply kill X, but reboot usually applies changes better, IMO.)

---

