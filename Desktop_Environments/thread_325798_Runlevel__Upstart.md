---
title: "Runlevel / Upstart"
date: 2006-12-26
forum: Desktop Environments
---

### Post by Zeek00 on 2006-12-26
I've been looking around for a while to change my runlevel. I want to upon boot be thrown into a console so I have to manually start X. I'm trouble shooting my new ATI radeon graphics card. I'm sitting in recovery mode because it is the only thing that lets me into X. 

I need a method to do this that I can start from a recovery mode command shell. I understand that Edgy doesn't have or use the inittab. I can't use the system->admin->services menu so don't link me to a help file that tells me thats the method. Finally I can boot the normal way and get the load screen and that is as far is I can get so not going to be able to change it from the login screen.

Any help greatly appreciated.

Zeek

---

### Post by christhemonkey on 2006-12-26
To change runlevels, you can use the command init:

```
sudo init 1 
```
This will switch you to the runlevel 1, (single user mode)


To make this automatic at bootup you need to edit this file, /etc/inittab

Make it look something like this:
```
# Default runlevel. The runlevels used by RHS are:
# 0 - halt (Do NOT set initdefault to this)
# 1 - Single user mode
# 2 - Multiuser, without NFS (The same as 3, if you do not have networking)
# 3 - Full multiuser mode
# 4 - unused
# 5 - X11
# 6 - reboot (Do NOT set initdefault to this)
# 
id:3:initdefault:                         # Console Text Mode
#id:5:initdefault:                         # Console GUI Mode
```

---

### Post by Zeek00 on 2006-12-26
Are you telling me to create a inittab file because no such file exists in Ubuntu Edgy. Changing runlevel using init num doesn't work. They all load the same set of files I believe. And isn't that for a one time use only? 

Default runlevel is 2 on edgy. I've disabled the gdm on runlevel 2 but doesn't do anything.

---

