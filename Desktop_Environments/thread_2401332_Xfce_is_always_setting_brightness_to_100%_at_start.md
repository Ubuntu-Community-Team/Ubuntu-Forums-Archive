---
title: "Xfce is always setting brightness to 100% at start"
date: 2018-09-17
forum: Desktop Environments
---

### Post by tigrezno on 2018-09-17
I want Xorg to start with a brightness setting of 0.5.

I've succeded at configuring lightdm in **/etc/lightdm/lightdm.conf** with the **display-setup-script** directive.

But I have failed to configure Xfce. I've tried launching the brightness script from the **Session & Startup** settings but didn't work. 
Also tried **/etc/X11/Xsession.d/** without success.

The script actually executed but something else is setting the brightness again at 100% after that.

I'm so mad at it that I'm on the verge to uninstall xfce and use other DE.

[note] I'm using xrandr since xbacklight doesn't work. I'm on a desktop PC.

[SOLVED] Somehow. I just added a .desktop file with the script in ~/.config/autostart. It's executed AFTER xfce sets the brightness to 100%, so it works. For a few milliseconds there is a flash, but that's all.

[EDIT] Ok, I found the real culprit. It was nvidia-settings being loaded by xfce. I had to set the brightness in the nvidia-settings GUI. That fixed the issue.

---

### Post by yetimon_64 on 2018-09-17
> **tigrezno said:**
> ...
I'm so mad at it that I'm on the verge to uninstall xfce and use other DE.

[note] I'm using xrandr since xbacklight doesn't work.** I'm on a desktop PC**.
I have bolded the last comment in your post. It stood out the most here on reading the post.

On a desktop PC that situation actually sounds right. I have never known of a desktop pc that didn't set the brightness at 100% all the time.
I have only ever seen the screen brightness lowered in xfce on laptops, never on a desktop installation of xfce here and I've had a few on each type of system.

If you are on a desktop, usually that would indicate a monitor plugged in via either a VGA or HDMI cable. Most external monitors I've ever seen or used require the brightness to be set in the monitor's menu itself, either via a remote control or buttons on the monitor itself, NOT from the OS or DE as it sounds like you are trying to do.

If you really are trying this on a desktop PC with a normal monitor and not on a laptop you seem to be trying to set up an impossible situation (and poor ol' xfce is copping the blame :lol:). Cheers, yeti.

---

### Post by The Cog on 2018-09-17
I use redshift to alter the colour of my monitor in the evenings, it that helps at all.

---

