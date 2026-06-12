---
title: "idesk problems, help wanted/needed"
date: 2009-05-28
forum: Desktop Environments
---

### Post by Wim De Winter on 2009-05-28
Ok, a summary of what I've been doing so far. To start with, I made a 2nd partition to tinker around with. I did a minimal alternate Hardy install on it,just the basics, and added fluxbox and idesk amongst others. I then wanted to create some desktop icons to direct me to some applications and to shutdown. The shutdown thingies proved to be the major obstacle, so here's a mini howto on how I worked things out. My aim was to get desktop icons to double-click on so the shutdown or reboot sequence would start. The following procedure workd for me ...

To add a reboot menu shortcut in the standard .fluxbox/menu, add this:

> [exec] (Reboot) {xterm -e sudo /sbin/shutdown -r now}

-r will reboot whereas -P will powerdown.

The following part would be to create the .lnk file that has to be placed in the .idesktop folder:

> 
table Icon
[INDENT]Caption: Reboot
ToolTip.Caption: opnieuw opstarten
Command: sudo /sbin/shutdown -r now
Icon: /usr/share/icons/logoff/logoff-oranje.png
Width: 60
Height: 60
X: 170
Y: 1110[/INDENT]
end


Then add the bold lines to your sudoers file using ```
sudo visudo
```wim is my username and Desktop-Wim my hostname

> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset
Defaults        editor=/usr/bin/leafpad

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL
**wim     ALL=(ALL) ALL**

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
**wim Desktop-Wim = NOPASSWD: /sbin/shutdown**

A big thanks to everyone at the [Google Fluxbox Group]("http://groups.google.be/group/fluxbox")

---

### Post by hailtothethief on 2009-07-23
Hopefully, you read this. I made a simple utility to configure iDesk. It is available for download from [http://sourceforge.net/projects/ideskconfig/files/]("http://sourceforge.net/projects/ideskconfig/files/")

Just click the link that says ideskconfig-(something).tar.gz

Extract the tarball and double click idesk_config.py and choose run.

The latest version as of right now is 0.9, and will be updated frequently.

Good luck!

---

