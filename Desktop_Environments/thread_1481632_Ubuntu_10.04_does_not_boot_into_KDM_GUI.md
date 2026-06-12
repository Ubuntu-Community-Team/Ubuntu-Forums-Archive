---
title: "Ubuntu 10.04 does not boot into KDM GUI"
date: 2010-05-12
forum: Desktop Environments
---

### Post by jdaniels on 2010-05-12
Hi,

I have just installed Ubuntu 10.04 onto am IBM Thinkpad (not sure of the exact make). It all basically works but I cannot get it to boot into the GUI at startup. I have done the following (generally as root), followed by a restart in each case:


[LIST]
[*]set runlevel to 5 (since found out this is irrelevant to GUI's in Ubuntu)
[*]added sysv-rc-conf and used it to set KDM and GDM to X in runlevels 2 3 4 and 5
[*] verified I am in an appropriate runlevel with who -r - I am in 5 at the moment
[*]installed Gnome and KDE with apt-get - that worked
[*]tested Gnome, KDE and startx init scripts / services from the command line (they all work OK)
[*]executed dpkg-reconfigure xserver-xorg (it did nothing)
[/LIST]
The laptop will boot into the tty1 command line login prompt with no trouble, and from there I log in as root, execute 'service kdm start', then hit ctrl-alt-f7 and get to the GUI that way. Ordinarily that would do, but this is for my mum (she trashes windows like a looter) so she's getting Ubuntu now, but if I could have it "just boot" into the KDM (I would prefer to use this as the default GUI) that would be great and save me alot of stressed phone calls.

One more thing is that I don't seem to have /etc/X11/xorg.conf (I copied /etc/X11/xorg.conf.failsafe to /etc/X11/xorg.conf but no difference)

So come on Ubuntu Forums - make an old lady happy ;)

Cheers,
Jon

---

### Post by HighmanIRL on 2010-06-21
I think I have the same problem. I have just installed ubuntu 10.04. At the end of the install it ejected the cd and proceeded to reboot my computer only to be met with a text login prompt and GUI?? I am a complete newbie to Ubuntu and would appreciate any help.

---

### Post by HighmanIRL on 2010-06-21
I think I have the same problem. I have just installed ubuntu 10.04. At the end of the install it ejected the cd and proceeded to reboot my computer only to be met with a text login prompt and GUI?? I am a complete newbie to Ubuntu and would appreciate any help.

---

### Post by HighmanIRL on 2010-06-21
I think I have the same problem. I have just installed ubuntu 10.04. At the end of the install it ejected the cd and proceeded to reboot my computer only to be met with a text login prompt and GUI?? I am a complete newbie to Ubuntu and would appreciate any help.

---

