---
title: "user switcher error after moving /home"
date: 2008-10-24
forum: Desktop Environments
---

### Post by dave.com on 2008-10-24
Recently I re-mounted the /home partition back onto my fresh Ubuntu installation. Version now is HH (8.04) - Ubuntu - kernel 2.6.24-21 (Desktop ed.n). After the system updated from 2.6.24-19 and my grub menu.lst was sorted out, fstab sorted out, the box lost its bearings. 

(I fixed this): 
**(ntfs-config: 5719): WARNING ** : Error: could not connect to dbus: org.freedom.desktop.DBUS.Error.FileNotFound Failed to connect to socket /var/run/dbus/systembus.socket: No such file or directory
**(ntfs-config: 5719): WARNING ** : Error: An error occurred when trying to initialize HAL. Can't search for new partition."
 
Next was /etc/gdm/Xsession (this needs your help):
" **(seahorse-agent: 6703): libgnomevfs- WARNING ** : Unable to create ~/.gnome2 directory: Permission denied. Could not create per-user gnome configuration directory "/home/<user>/.gnome2/: Permission denied"

I ran Recovery session and ended up at a terminal. From there checked /home permissions and set chown user:user /home/user with permissions 644. Now I had trouble with X and nvidia-xconfig. Somehow got into Desktop (privileged session) and re-checked 3rd Party Proprietary Device thingummy and did X-Server setup stuff. 

But the problems were not over: "user switcher error" 
> ~/.Xauthority file badly configured or missing
100 not authenticated
Your user doesn't have permissions to create additional logins. Check your ~/.Xauthority setup

Re-Starting Ubuntu, results: 
This error only allows X to start after I remove /tmp/X0-lock from a tty console. The user login then escalates to privileged session as root. Ubuntu launcher reports /home/user/.dmrc is being ignored (~/.Xauthority bad). This "privileged" session does not have net connection and appears unwilling to allow setting it (damn my router-modem ;p). I have no idea what permissions are wrong ..and I thought I had 'fixed' them...

---

### Post by dave.com on 2008-10-24
Made a new user, restarted comp, logged in new user and changed home directory and user directory/file permissions.

---

