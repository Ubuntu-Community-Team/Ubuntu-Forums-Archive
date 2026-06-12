---
title: "Change the default user in Ubuntu Gnome login screen"
date: 2013-12-20
forum: Desktop Environments
---

### Post by morningstar.fallen on 2013-12-20
Hi everyone,

I have a Ubuntu Gnome 13.10 (x64) box joined to an AD domain. After joining and logging in with a domain account several times , it still displays the local user as the primary option on the login screen after reboot. I have followed the guide below to fix this but to no avail:

[http://bit.ly/1dqOnHi](http://bit.ly/1dqOnHi)

```

[greeter]
# If true show all the users, if false show the last connected users
IncludeAll=false
# User to always show in the user list
Include=mandel

```

Any idea how to get the domain user "mandel" to display as default?

---

### Post by ibjsb4 on 2013-12-21
You can’t use that link, it too old.  Those settings are for gnome display manager (gdm), you are running lightdm.  I do not run a DM so I be a little rusty on this, but ..
 
I think you need to add the lines below to /etc/default/grub
 
```
autologin-user=[COLOR=#ff0000]USERNAME[/COLOR]
autologin-user-timeout=0
``` 

 then ..
 
```
sudo update-grub
``` 

 I did find this that uses /lightdm.conf.
 
[http://ubuntuforums.org/showthread.php?t=2163669&p=12737061&viewfull=1#post12737061](http://ubuntuforums.org/showthread.php?t=2163669&p=12737061&viewfull=1#post12737061)

---

### Post by morningstar.fallen on 2014-01-17
Hi, sorry for a late reply. It unfortunately did not work.

But am I right thinking that this should be a change done in gnome configuration rather than in bootloader/grub?

---

### Post by steeldriver on 2014-01-17
I don't know how to make the box show the last (domain) login, but if you're using lightdm you should be able to suppress the user list by setting the greeter SeatDefaults in the lightdm.conf file

```

$ cat /etc/lightdm/lightdm.conf

[SeatDefaults]
greeter-session=unity-greeter
session-setup-script=/usr/local/bin/mount_windirs.sh
allow-guest=false
user-session=xubuntu
[B]greeter-hide-users=true
greeter-show-manual-login=true
[/B]
```

You can either manually edit the file or use the lightdm-set-defaults utility

```

sudo /usr/lib/lightdm/lightdm-set-defaults **--hide-users --show-manual-login**

```

---

### Post by morningstar.fallen on 2014-01-22
[FONT=arial]That didn't help either. There isn't any "lightdm.conf" file present in the "/etc/lightdm" directory. Only a subdirectory "lightdm.conf.d", containing a file called "20-gnome.conf".

It only contained the following lines:
[/FONT]
[SeatDefaults]
user-session=gnome
[FONT=arial]
So I've tried to add the following below:[/FONT]

greeter-hide-users=true
greeter-show-manual-login=true

[FONT=arial]And rebooted. But Gnome still shows the local admin as the default login.[/FONT]

---

