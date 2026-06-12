---
title: "Desktop effects not enabling"
date: 2008-03-23
forum: Desktop Effects &amp; Customization
---

### Post by tuxb0y on 2008-03-23
hi
i just setup a new box with Ubuntu 7.10 on it i did all the updates, installed envy which futher installed driver for my ati card and installed catalyst. ok my problem is that when i go to enable desktop effects it wont let me. it tells me that composite extension are not available. so i go into my xorg.conf and change a value called section extension to enable i then reset x server and i try to enable desktop effects and it tell me there not available. i know catalyst and my driver are working cause im running @ 1680 by 1050 and i can open catalyst without errors. byt he way i also installed compiz manager

please help

---

### Post by tuxb0y on 2008-03-23
never mind fixed it lol
just had to reinstall driver :p should of tried that first
o well

---

### Post by Dr_VidoKifla on 2008-03-23
Hi, I just installed new ubuntu 8.04 and I can enable full vizual effects in the appearance menu. Can some one please help me to resolve this problem, there are no updates to download? 


TNX

---

### Post by Ub1476 on 2008-03-23
> **Dr_VidoKifla said:**
> Hi, I just installed new ubuntu 8.04 and I can enable full vizual effects in the appearance menu. Can some one please help me to resolve this problem, there are no updates to download? 


TNX

Hi, I suppose you mean you **can't**? If so, what error do you get when you try to enable Visual Effects? Is it ATI or Nvidia graphic card? Have you install drivers from System>Administration>Hardware Drivers? Note that Hardy is still in Alpha/Beta so it's not assured to work correctly.

---

### Post by Dr_VidoKifla on 2008-03-23
Yeah, that is what I mean. I have ATI 9600Pro, I have installed all driver, there are no new updates to install. The problem appear when I go to the apearance preferences and I click on the extra effects, it pops this message "The Composite extension is not available". Do you know what should I do?

---

### Post by Ub1476 on 2008-03-23
You'll need to install XGL (this wont be necessary in Ubuntu 8.04 because the new drivers support Linux much better).

To install, search for XGL (xserver-xgl) in Synaptic package manager or install through Terminal with:

```
sudo apt-get install xserver-xgl
```

Logout and login for the change to take effect.

---

### Post by Dr_VidoKifla on 2008-03-23
Well every thin works now whit the visualisation but a new problem appears
 "ere was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The Settings Daemon restarted too many times.

GNOME will still try to restart the Settings Daemon next time you log in."

Any solutions?

---

### Post by Dr_VidoKifla on 2008-03-23
BTW Every time i restarts it shows this problem so restart is not the solution.

---

### Post by Ub1476 on 2008-03-23
Does this happen if you use the default theme?

---

### Post by Dr_VidoKifla on 2008-03-23
I did not change anything, theme changed a bit when I installed compiz fusion, when I try to open appearance tab i pops.

Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

---

### Post by Ub1476 on 2008-03-23
See [here]("http://ubuntuforums.org/showthread.php?t=579167").

---

