---
title: "Enter password for default keyring to unlock"
date: 2009-09-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bryan_btb on 2009-09-16
I am a newbie to ubuntu. I installed last night and was running everything great. when I shutdown last night I didn't log off first, i have ubuntu set to auto login, when i powered on this morning i am getting:
Enter password for default keyring to unlock
The application "NetworkManager Applet" (/usr/bin/nm-
applet)wants access to the default keyring, but is locked.

My password will not work. Is there a way around this?

Thank you,
Bryan

---

### Post by SonicsDemon on 2009-09-16
Hm, Idk. Try going to system->administration ->network, highlight your devices and put a checkmark in the box "allow users to enable/disable devices"
I also found a thread here but it may be a little complex, but if you can make heads and tails of it, more power to you.
[http://forums.fedoraforum.org/showthread.php?t=184442]("http://forums.fedoraforum.org/showthread.php?t=184442")

This seems like a security issue with your router, maybe you could also remove the security temporarily and try connecting.
 
Hope this helps!:)

---

### Post by cranecreek on 2009-09-16
I have the Dell Studio XPS and it ask me every time for the key ring to access my wireless router. Kind of a pain but it does help you remember the passwd. If you don't remember the passwd then rest your router and set it up again.

---

### Post by Dennis N on 2009-09-16
cranecreek;

Just a comment:

If setup your keyring password for the wireless network to be the same as your Ubuntu login password, you should not need to log in separately to the router every time. Connection is automatic. This has always worked for me.

---

### Post by Boondoklife on 2009-09-16
This is cause you have setup the autologin, just go into the network manager and edit the wifi connection. In there will be a checkbox for available to all users, check it and then reboot. You should not be prompted.

---

### Post by Vschelkanov on 2009-10-12
Try the following to rollback to the previous version:
 aptitude purge gconf2

---

### Post by MC707 on 2009-10-31
> **Boondoklife said:**
> This is cause you have setup the autologin, just go into the network manager and edit the wifi connection. In there will be a checkbox for available to all users, check it and then reboot. You should not be prompted.

Awesomeness. That worked for me, that prompt every boot was becoming annoying. Thanks.

---

