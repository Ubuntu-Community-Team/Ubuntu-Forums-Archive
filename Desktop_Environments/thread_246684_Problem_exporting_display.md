---
title: "Problem exporting display"
date: 2006-08-29
forum: Desktop Environments
---

### Post by Saubazi on 2006-08-29
I have a remote linux machine running KDM. I am trying to login with ssh and then start the konqueror on my screen from it.

I give export DISPLAY=192.168.178.22:0.0 and then konqueror - on this machine I give xhost +. I get: konqueror: cannot connect to X server 192.168.178.22:0 as an answer?

I have tried putting true for [xmdcp] in /etc/gdm/gdsm.conf and DisallowTCP=False

So beats me - I don't know what else I could still try to get it running
(yes I restarted x after changes - still no go)

---

### Post by apolyak on 2006-08-29
just a minute ago repled to simuilar question, look at "GUI remote control of server programs" [http://www.ubuntuforums.org/showthread.php?t=246589](http://www.ubuntuforums.org/showthread.php?t=246589)

---

### Post by Saubazi on 2006-08-30
Sorry but that article is not really the answer.
I have done it on KDE and I more or less know what 
to change in the respective kdm configuration files. 
My problem is achieving it with gdm - the changes I've done
do not seem to be enough and mere xhost + and export DISPLAY won't cut it - the connection is blocked at some other place.

---

### Post by apolyak on 2006-08-30
on local PC to allow recieving of forwarded X (using menu): System-Login_Window-Security and uncheck Deny TCP connections to Xserver.

on local PC: xhost +
(it is more secure to use: xhost + xxx.xxx.xxx.xxx_of_remote_PC)

ssh -X user_name@host_name_remote_PC

on remote PC: export DISPLAY=xxx.xxx.xxx.xxx:0.0 (where xxx.xxx.xxx.xxx is for local PC)

on remote PC: konqueror &

assuming firewall is off or ssh port is open.

hope this helps

---

