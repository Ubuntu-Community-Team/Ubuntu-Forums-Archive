---
title: "Installed XFCE - changed system branding"
date: 2010-05-22
forum: Desktop Environments
---

### Post by epp on 2010-05-22
I originally installed ubuntu on a machine, beginning with 7.10, then to 8.04 LTS, then to 10.04 LTS.  Because of a change to an IDE/SCSI driver sometime in 2008, no distro released from the autumn of 2008 onward will install on this machine (Compaq Presario 5900Z) directly.

I installed the XFCE desktop on this machine last night and afterwards, it changed the branding.  The initial ubuntu splash screen now comes up as xubuntu along with the blue xubuntu graphics at login.

Should that have occurred?  

And also, if I switch the desktop environment at the login screen back to GNOME, does the initial splash screen also change back to ubuntu (with their graphics) at the next bootup?

---

### Post by XubuRoxMySox on 2010-05-22
It sounds like you installed xubuntu-desktop rather than Xfce-4.

That's where the branding came from.

You may log into to either Gnome or Xfce, but the boot screen probably defaulted to Xubuntu because it is part of the xubuntu-desktop package. It may remain so (on start-up, before choosing a session (either Gnome of Xfce), but that shouldn't matter. If it does you can always remove xubuntu-desktop and replace it with "plain vanilla" Xfce-4.

Hoping that helps,
Robin

---

### Post by epp on 2010-05-22
I just checked the Synaptic Package Manager, the package *xubuntu-desktop* itself, is not installed.  

Packages installed with *xubuntu* in the name are:

[LIST]
[*]xubuntu-icon-theme
[*]xubuntu-artwork
[*]xubuntu-plymouth-theme
[*]xubuntu-wallpapers
[*]xubuntu-gdm-theme
[/LIST]

I installed the *xfce4* meta package as well as *xfce4-goodies*, one of these must have changed the branding after the install.  

In any event, XFCE does run faster than GNOME on this hardware.  :)

---

### Post by stanca on 2010-05-22
It's the xubuntu-plymouth and gdm theme.

---

