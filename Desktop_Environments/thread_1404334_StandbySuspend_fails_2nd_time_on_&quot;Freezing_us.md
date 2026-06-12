---
title: "Standby/Suspend: fails 2nd time on &quot;Freezing user processes...&quot;"
date: 2010-02-11
forum: Desktop Environments
---

### Post by browneej on 2010-02-11
I have what I think is a somewhat different failure of standby than I've seen listed on other threads, and I'm stumped.  I get the following characters during the standby process:

[xxxx:xxxxxx] Freezing user space processes...

The system hangs on this for a while, then comes back to the login screen without going into standby.  This ONLY HAPPENS on a SECOND standby attempt--the first standby after booting ALWAYS succeeds.  The standby log doesn't indicate any failures.  

I had made other changes previously that temporarily got standby working consistently:

/etc/default/grub:  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.[COLOR=Red]**autosuspend=-1**[/COLOR]"

/etc/default/acpi-support:  
POST_VIDEO=false
SAVE_VBE_STATE=FALSE
SAVE_VIDEO_PCI_STATE=true

nvidia-settings: sync to vblank = false (unchecked)

I am running 
Ubuntu 9.10 amd64
nvidia 8800GT w/ TWINVIEW dual screen
compiz, occasionally emerald
gnome-do and cairo-dock
VirtualBox 3.12

I'm totally stumped.  I've seen some threads out there about FUSE and USB, but those issues SEEM to be cleared up 1-2 years ago.  Most threads deal with resuming with a blank screen (which I've had on my nvidia laptop!) or failing to suspend period.  This problem seems to almost get there, then boom.  There are LOTS of threads on this, so maybe I missed something buried on page 35 of one the threads ;)

Any help would be greatly appreciated.

Tail of /var/log/pm-suspend.log:

> 

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
/etc/pm/sleep.d/10_grub-common suspend suspend: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
Thu Feb 11 08:58:23 CST 2010: performing suspend
Thu Feb 11 08:58:48 CST 2010: Awake.
Thu Feb 11 08:58:48 CST 2010: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend: success.
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume suspend: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode resume suspend: success.
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
/etc/pm/sleep.d/10_grub-common resume suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk resume suspend: success.
/usr/lib/pm-utils/sleep.d/000record resume suspend: success.
Thu Feb 11 08:58:49 CST 2010: Finished.

---

### Post by elitenoobboy on 2011-03-18
Does trying the 2.6.38 kernel from here [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
 fix this? That kernel for natty should have some usb suspend patches in it that might fix the problem.

---

