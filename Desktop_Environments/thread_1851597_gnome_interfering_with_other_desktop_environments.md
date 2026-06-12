---
title: "gnome interfering with other desktop environments"
date: 2011-09-28
forum: Desktop Environments
---

### Post by astrobob.tk on 2011-09-28
Hello there,

I've recently installed each of fluxbox, openbox, blackbox, lxde & i think xfce. My default desktop  is gnome with screenlet & guake set to launch at startup.

Anyhow, the thing is that when I log in to either of the other environments, most notable lxde & openbox, the screenlets & guake are launched & this causes some weird changes in the GUI.

My questions:

1) is it wrong to install several environments for the same system ?
2) what can I do to keep the default of each environment unless I otherwise change it ? (i.e.; i do not want screenlet & guake to launch under the other environments)

thanks in advance

---

### Post by 3Miro on 2011-09-28
> **astrobob.tk said:**
> 

1) is it wrong to install several environments for the same system ?
2) what can I do to keep the default of each environment unless I otherwise change it ? (i.e.; i do not want screenlet & guake to launch under the other environments)

thanks in advance

1. NO. Especially if you are new to Linux, you should absolutely install different DE so  you can try them all and find what works best for you.

2. I am not sure how the autostart apps are handled by the different DE. I know that XFCE has the habit of remembering everything that is running. You can try to disable the unwanted apps from the xfce4 session settings to see if this would help. 

Otherwise, you can probably make a script that would detect which DE you are running and then start the apps accordingly.

---

### Post by astrobob.tk on 2011-09-29
> **3Miro said:**
> 

2. I am not sure how the autostart apps are handled by the different DE. I know that XFCE has the habit of remembering everything that is running. You can try to disable the unwanted apps from the xfce4 session settings to see if this would help. 

Otherwise, you can probably make a script that would detect which DE you are running and then start the apps accordingly.

Well, I logged into xfce (w/ Docky, Avant Window Navigator, guake, & several other applications including screenlet). I used the "Desktop Settings" from the Control Center & un-checked those applications & rebooted. They still do launch on startup :S (i also tried unchecking the remember part on my way loggin out but it doesn't make any difference)

Moreover, just sometimes, when I launch into my default Gnome session, xfce (in its graphical menus; i.e.; just the menue's & the window themes) takes over those of gnome!

This conflict doesn't happen w/ openbox, blackbox& fluxbox. Only with xfce & lxde!


As for writing a script; I don't know any scripting. Will sometime in the future.

Any ideas ?

---

### Post by szpuni on 2011-09-29
Hey I have similar issue with Gnome.

There is configuration file for all your autostart in gnome located in your home directory > ~/.config/autostart
This contain all settings from your autostart on graphical interface.

But yes for some reason after i have switched gnome for openbox i saw that some of startup items are executed for some reason in background and I can't even see that process.

Example:
I have python script for my touchscreen as build in one do not work at all and I had gnome autostart item which ran this script on screen session.
Since i have switched to open box this is not executed as there is no screen session but my touscreen is working as it should and few other settings like disabling touchscreen device is enabled as well (other command in gnome startup session).

So why this is happening at all if gnome do not start at all?
I suppose there is some glitch in startup process configuration.

In addition sometimes openbox is not starting at all even if you force startup with openbox in gdmsetup.

I still have gnome starting instead of openbox which is set in gdmsetup.

Any ideas?

---

