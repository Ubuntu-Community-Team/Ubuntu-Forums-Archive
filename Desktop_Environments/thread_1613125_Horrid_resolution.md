---
title: "Horrid resolution"
date: 2010-11-04
forum: Desktop Environments
---

### Post by @lpha on 2010-11-04
**Hi**, I have a problem where the resolution during bootup, shutdown, switching users, and the theme icons look very grainy & cheap. It might have started when I booted in failsafe graphics mode and after that, it never went away. Could be wrong about how it happened but **is there a way to get out of failsafe mode? Or a way to reconfigure default, normal graphics? **




**Thank you very much** in advance, guys.

---

### Post by Peter09 on 2010-11-04
Can you post the output of the terminal command
 
```
lshw -C video
```
 
also check in
 
System->Preferences->Display
 
you may be able to set your resolution there.
 
Also Check
 
System->Administration->Hardware
 
see if there is a graphics driver that needs enabling.

---

### Post by @lpha on 2010-11-04
_[SIZE=1]**lshw -C video:**[/SIZE]_
*-display               
       description: VGA compatible controller
       product: RS480 [Radeon Xpress 200G Series]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=64 mingnt=8
       resources: irq:17 memory:f8000000-fbffffff ioport:ee00(size=256) memory:fdef0000-fdefffff memory:fde00000-fde1ffff



Display and hardware settings are set correctly but problem still persists. I should also note that I changed a "xorg" file in the terminal trying to solve a system freeze (now fixed), maybe that caused a problem.

---

### Post by Peter09 on 2010-11-05
I presume that you are running lucid or above, try removing the xorg file (save it by renaming it). Then reboot and see if things improve.

---

### Post by @lpha on 2010-11-06
I edited xorg file using:** sudo gedit  /etc/X11/xorg.conf** to file name: **xorg.conf1** in texteditor and Ubuntu won't even boot up. I am in failsafe mode as of now. Please help me undo this.

---

### Post by Peter09 on 2010-11-06
OK,
just to confirm what you did,
you edited xorg.conf and saved it as xorg.conf1. Did you delete the original xorg.conf?

To get back to where you started, hold the shift key down while the system is booting, this should get you to the recovery menu. Selcect reconfigure graphics and let it do what it can to reboot.

If you get to the desktop check the System->Admin->Hardware menue.

---

### Post by @lpha on 2010-11-06
Hey thanks. Reconfiguring the graphics fixed it, that was a simple  solution. I guess I just panicked and couldn't think clearly but I'm up  & running now. Thank you..


> **Peter09 said:**
> OK,
just to confirm what you did,
you edited xorg.conf and saved it as xorg.conf1.

Correct, all I did was rename the xorg file through the command line. Was this the right way to do it?

Also, when I go to my **etc/X11/** folder, I don't see a normal **xorg.conf** file. The only thing I see with the name xorg are** xorg.conf.failsafe** and **xorg.conf-backup **files.

---

### Post by Peter09 on 2010-11-06
These days Ubuntu does not normally run with an xorg file, although for some special retirements one can be built. Sometimes an old xorg.conf file is what screws up the graphics setup.

---

### Post by @lpha on 2010-11-06
How can I get rid of xorg safely?

---

### Post by coffeecat on 2010-11-06
You mean xorg.conf. You have already by renaming it. There is no xorg.conf file now in your /etc/X11/ folder.

---

### Post by @lpha on 2010-11-06
> **coffeecat said:**
> You mean xorg.conf. You have already by renaming it. There is no xorg.conf file now in your /etc/X11/ folder.

The reason I said this was because the normal xorg.conf file was never in the /etc/X11/folder, even before I renamed it. All that was there before I did the editing was the xorg.conf.failsafe, & that's the file I think is causing the big problem. What do you guys recommend me doing?

Should I _remove_ or _reconfigure_ xorg.conf.failsafe? Are there more options? I know xorg is the culprit for the resolution bug.

---

### Post by Peter09 on 2010-11-07
If its working now, just leave it, the other two files are there for recovery reasons, not normal working.

---

### Post by coffeecat on 2010-11-07
> **Peter09 said:**
> If its working now, just leave it, the other two files are there for recovery reasons, not normal working.

Agreed.

> **@lpha said:**
> The reason I said this was because the normal xorg.conf file was never in the /etc/X11/folder, even before I renamed it. All that was there before I did the editing was the xorg.conf.failsafe, & that's the file I think is causing the big problem. What do you guys recommend me doing?

Should I _remove_ or _reconfigure_ xorg.conf.failsafe? Are there more options? I know xorg is the culprit for the resolution bug.

xorg.org.failsafe is doing nothing. [xorg or Xorg or X.org](http://en.wikipedia.org/wiki/Xorg) is not the culprit for anything because xorg is just another name for the xserver which is the underpinnings for your whole GUI. xorg.conf is the configuration file that used to be used by xorg/xserver. Within the last two to three years, the xorg people have developed xserver to be able to autodetect and autoconfigure most hardware so long as you are using one of the open-source drivers. You are using the radeon driver, which is an open source one. As Peter09 said earlier, an xorg.conf is only needed for special requirements, such as a proprietary video driver. If an xorg.conf file is present, it will take priority over any autoconfiguration, which is why a bad xorg.conf file can mess up the graphics.

Leave the two xorg.conf* files or delete them. They are doing nothing except taking up a few kilobytes of hard drive space. But you might want to keep them, particularly the *failsafe one, even if only for reference or interest.

---

### Post by @lpha on 2010-11-07
Thank you guys for the feedback. The resolution problem that I first posted still remains, though (screen flicker when switching users, bad resolution on boot & shutdown, and theme icons are hardly visible). What could the problem be if it has nothing to do with this "xorg"?




Sorry if I seem to be a bug. This post turned out to be much longer than I anticipated.

---

### Post by coffeecat on 2010-11-08
> **@lpha said:**
> theme icons look very grainy & cheap.

Post a screenshot so that we can see what you mean.

What model laptop is it? What is its maximum resolution according to specification? What resolution is showing when you go to System > Preferences > Monitors? If that is not the maximum resolution, is it shown in the drop-down box for resolution?

> **@lpha said:**
> What could the problem be if it has nothing to do with this "xorg"?

To exclude failing hardware, boot up with the live CD and see whether the problems remain. You can't switch users but you can log out and in again. Log in details for the live session are "ubuntu" for username and blank for the password - that is, simply press enter when prompted for password.

---

### Post by Peter09 on 2010-11-08
Are you talking about resolution on your desktop or resolution during startup/shutdown. Also you seem to be talking about icon problems. Have you tried changing your theme using System->Preferences->Appearance.

---

### Post by @lpha on 2010-11-08
Heres what things look like in boot menu as well (grainy):
[ATTACH]175054[/ATTACH]

I actually have a desktop, not a laptop.. and the max resolution for my screen is 1280 x 1024. I'm using that setting. I'll also try out the live cd and post my results as soon as possible.


Peter, I am talking about the resolution during startup/shutdown. The worst problem is when I switch users. The screen flickers and it is difficult to log in. Unfortunately, I couldn't get a screenshot of those.

---

### Post by Peter09 on 2010-11-09
Hi,
if you are talking about the screen where you see the Ubuntu logo and the dots moving, then this is not controlled by Gnome/X at all but by Plymouth(I think) which is started prior to you logging in.  I do not know how to adjust the resolution for that.
 
If you have a desktop which is running at the correct resolution than thats a good start. As for your problems with switching users, this still sounds like a graphics driver/card issue.
 
Do you see any problems on your normal desktop when moving windows etc?

---

