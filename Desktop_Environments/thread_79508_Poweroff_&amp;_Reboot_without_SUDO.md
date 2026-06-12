---
title: "Poweroff &amp; Reboot without SUDO"
date: 2005-10-20
forum: Desktop Environments
---

### Post by superr on 2005-10-20
Hi, i'm new to ubuntu! :oops: 

I'd like to have permission to execute (without sudo) both commands: *poweroff* and *reboot*! I've tried this (unsuccessfully):
[quote="FILE: /etc/sudoers"]
# Host alias specification

# User alias specification

# Cmnd alias specification
Cmnd_Alias REBOOT = /sbin/reboot
Cmnd_Alias POWEROFF = /sbin/poweroff
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
superr  ALL = REBOOT
superr  ALL = POWEROFF

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL
[/quote]

PS: By the way, is there anyway to have xmms as the multimedia default application? (so i can control it with my keyboard hotkeys). ;)

---

### Post by superr on 2005-10-20
Can anyone help me? :oops:

---

### Post by objorkum on 2005-10-20
You should use the "shutdown"-command when powering off or rebooting.

Power off:
shutdown -h now

Reboot:
shutdown -r now

So I think your solution should be to set the "shutdown"-script SUID, so try this:

sudo chmod u+s /sbin/shutdown

Then try to use shutdown as a regular user.

---

