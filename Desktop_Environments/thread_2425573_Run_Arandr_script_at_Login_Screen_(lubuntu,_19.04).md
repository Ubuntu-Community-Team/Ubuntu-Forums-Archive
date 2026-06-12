---
title: "Run Arandr script at Login Screen (lubuntu, 19.04)"
date: 2019-08-27
forum: Desktop Environments
---

### Post by jmsfnch2 on 2019-08-27
I'm trying to configure a spanned-desktop using 2 monitors attached to a USB dock, ignoring the on-board graphics adaptor.

So far I've managed to configure a spanned desktop using Arandr, but this requires me to log in and toggle this configuration (or execute a configuration script).

Unfortunately, at boot the default video output is directed to the on-board DVI output (disconnected), so I cannot see the login page to make these changes.  I don't want to configure auto-login to circumvent this.


To solve this, how do I:


[LIST=1]
[*]Preferred.  Trigger a script at the login page (i.e. to run the Arandr configuration and output over USB), or
[*]Set the default video output at boot so the login page appears on one of the USB screens.
[/LIST]

ta,
James

---

### Post by TheFu on 2019-08-27
If you use X11, then there is a config file in /etc/X11/xorg.conf, that can control many settings at boot time.  If the file doesn't exist, X11 is auto-configuring itself using defaults.  In the old days, we had to manually configure this (or a similar file) BEFORE any GUI would work. [https://www.x.org/releases/X11R7.6/doc/man/man5/xorg.conf.5.xhtml](https://www.x.org/releases/X11R7.6/doc/man/man5/xorg.conf.5.xhtml)

Here's how someone else set their default: [https://superuser.com/questions/546069/setting-primary-monitor-in-ubuntu-without-xrandr](https://superuser.com/questions/546069/setting-primary-monitor-in-ubuntu-without-xrandr)
The 
```
Option      "Primary" "true"
```
line seems to be the critical aspect.  The example shown in that link isn't complete and you almost definitely cannot just copy/paste it. 
In one of my other systems, the xorg.conf file used is actually /etc/X11/xorg.conf.d/20-nvidia.conf ...  any file in that directory which ends in .conf will be used. There is a manpage for xorg.conf.d which explains this and other details.

After login happens ... Use **xrandr**, but that won't help anything prior to login.  Put it into the autorun file for the DE.  In LXDE with openbox as the WM, that was ~/.config/openbox/autostart  It gets invoked just after login.  I don't think you can change any GUI related things on a per-userid basis until after login. 
I have no idea which file LXQt uses.  There are a few other files which are run at login for old-school people.  ~/.xinitrc is one, but whether it is used or not is controlled by the login manager and DE and WM.  Looks like LXqt uses sddm as the default login manager.  I didn't see any settings to control the default monitor, but it does control the first programs run just after login.
[https://manual.lubuntu.me/3/3.2/3.2.10/monitor_settings.html](https://manual.lubuntu.me/3/3.2/3.2.10/monitor_settings.html) might help. IDK.

I think the best solution would be  to use the xorg.conf.d/ file to set the default monitor connection. The specific iGPU would determine the required settings.

Sorry, I don't have a direct answer.  19.04 is too new for my needs.

---

### Post by jmsfnch2 on 2019-08-28
Very good pointers, ta very much.

I'll run with the recommendation to try editing the X11 configuration and will post back with results.

You are right: the configuration file is missing, but I intend to generate it with this suggestion <[https://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there](https://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there)>... once I have perfected the art of interrupting boot...

---

### Post by TheFu on 2019-08-28
I would just ssh in to edit files, but I don't think any GUI tool will connect to the correct X/Server. Instead they will try to connect to the X/Server on the machine you are typing on, which would only be useful if it had the exact same GPU.

If I need a GUI terminal, so I can run GUI programs on the remote machine, I'd use 
```
ssh -X userid@remoteserver program-to-run
```
This requires that my local system is running and X/server or the remote X/client won't be able to connect.
It also requires that sshd_config on the remote server allows X11Forwarding.

---

### Post by guiverc on 2019-08-28
I started this reply yesterday but got called away.  `sddm` in my experience puts the login/greeter screen on all displays (un-mirrored).  I find this useful as I regularly have screens turned off, and can login with only a single (any) screen turned on (*though I have to move the mouse to the login box on the turned-on screen and click to use that one should it not be the default; the 'default' `sddm` uses is usually off in my case*).

This is a huge clue I suspect, as you're not getting this at all (*and your issue*).  But I don't have any experience with usb-connected screens..

 I don't know the mechanics of how sddm or logins work, but I haven't noticed any changes from 18.10 to 19.10 as it stands now (though I could have forgotten..). On boot the layout of my screens is not as I have it configured post-login, but the same as I get for a 'live' qa-test, ie. possibly `sddm` it's own default or a file I've not located.

---

