---
title: "gnome-settings-daemon cannot start with radeon.modeset=1"
date: 2010-08-18
forum: Desktop Environments
---

### Post by Cuivienor on 2010-08-18
Hi,

I am currently running Ubuntu 10.04 on a computer with the very bad ATI Radeon X1250. I have a single monitor (HDMI output), which is a 1360x768 resolution Sony flat screen TV.

From the beginning, I had to disable modeset at startup with the nomodeset option, otherwise the system wouldn't boot up. I was also experiencing random freezes, as described in several forum threads. Searching into kernel bug fixes, I noticed that both problems were solved in kernel 2.6.34, so I installed it.

Using kernel 2.6.34, when I startup with modeset enabled (or load up the radeon module with modprobe radeon modeset=1 before loading gdm), then the screen is displayed properly with the proper resolution, everything seems to work. However, the theme is not the usual Radiance/Ambiance theme, but much more blocky, gray, and not very pretty. Icons are also incorrect (screenshot attached). 

If I try to start the Settings -> Preferences -> Appearance application, it starts up but warns me that gnome-settings-daemon was not able to start properly. Changing themes/disabling and enabling compiz, etc. do not help, the theme is incorrect.

When I run sudo gnome-settings-daemon from the command line, I get the following error:

yannick@yannick-desktop:~$ sudo gnome-settings-daemon
**
ERROR:gnome-rr-config.c:622:gnome_rr_config_new_current: assertion failed: (gnome_rr_config_match (config, config))

Similarly, if I run gnome-display-properties, I get the exact same error message and gnome-display-properties doesn't start.

This error will occur with and without compiz, and using sudo or not.

However, changing the resolution via xrandr from the command line works properly.

I have also installed kernel 2.6.35 backported from Maverick, but the problem persists. Besides the kernels, I am running Ubuntu 10.04 vanilla with the latest updates installed from the Update Manager.

Everything works properly when radeon.modeset=0.

The only similar bug I could find is the following, but it's pretty old (November 2009) and no progress seems to have been done on this.

[http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg361681.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg361681.html)

I also see that some Red Hat bug reports that look similar but are not identical:
[https://bugzilla.redhat.com/show_bug.cgi?format=multiple&id=620917](https://bugzilla.redhat.com/show_bug.cgi?format=multiple&id=620917)
[https://bugzilla.redhat.com/show_bug.cgi?id=620909](https://bugzilla.redhat.com/show_bug.cgi?id=620909)

Does anyone have any idea on this?

Thank you very much for your help,

Yannick

---

### Post by Cuivienor on 2010-08-22
Hi,

I solved my problem - my computer has several outputs: DVI and HDMI.

Quickly looking at the code, it seems that when modeset is activated, gnome-settings-daemon or gnome-display-properties will detect both outputs and try to set up both outputs even if only one screen is connected. This causes the problem.

Solving it was straightforward: get both DVI and HDMI connected to my TV (which I use as a monitor), in two different inputs. Once done, everything works like a charm.

This however is a bug in Gnome and I will file a bug report.

Thanks,

Yannick

---

