---
title: "Locked Out"
date: 2009-04-27
forum: General Help
---

### Post by OldManRiver on 2009-04-27
All,

Added a second user to my 8.10 Desktop and now get an error on each user when attempting "sudo su" or any sudo command saying:

"user is not in sudoers file"

Not seeing much about this out there.  Can you direct me?

Thanks!

OMR

---

### Post by coffeecat on 2009-04-27
That's probably because when you create a second or subsequent user in System > Administration > Users and Groups, they are not given administrative privileges by default. For the accounts in question, go to 'Properties' > 'User Privileges' tab and tick the Administer System box.

---

### Post by OldManRiver on 2009-04-28
Gee,

If I could do that and was not locked out I would not be asking here.  I'm going to have to re-install again, 2nd time in 2 weeks, if I can not solve this.

OMR

---

### Post by Nepherte on 2009-04-28
There's generally no need to reinstall at all. When booting, choose the recovery mode instead. You'll be left at a command line and there you can add your user to the sudoers with the command visudo.

---

### Post by OldManRiver on 2009-04-28
WHat???

Recovery mode???

No such thing on this box!!

Least it is not showing.

OMR

---

### Post by Nepherte on 2009-04-28
Hmm, well I'm not acually using Ubuntu, but there *used* to be some sort of fallback kernel/ recovery mode you could choose in the grub boot menu.

Anyways, if it's not there you can still use a live cd to mount your linux install and edit the necessary files (in this case /etc/sudoers).

---

### Post by nandemonai on 2009-04-28
> **OldManRiver said:**
> Gee,

If I could do that and was not locked out I would not be asking here.  I'm going to have to re-install again, 2nd time in 2 weeks, if I can not solve this.

OMR

Have you tried System -> Administration -> Users and Groups with your **original** user? Unlocked and then modified the users in question that way?

---

### Post by freonchill on 2009-04-28
are you typing in "sudo su command" or "sudo command"

if the former, its just sudo + command

---

### Post by bapoumba on 2009-04-28
To make it clear, do you get sudo problems with both the first user created when installing ubuntu and the second?

To boot in recovery mode, you need to do it at the grub menu, there is a line below your regular kernel line. If you do not see the menu, hit escape when booting.

Then:
```
adduser <username_here> admin
reboot
```

---

### Post by OldManRiver on 2009-04-28
> **nandemonai said:**
> Have you tried System -> Administration -> Users and Groups with your **original** user? Unlocked and then modified the users in question that way?

Yup, and can not even open the session, always get the error,so that is why I posted.

OMR

---

### Post by OldManRiver on 2009-04-28
> **freonchill said:**
> are you typing in "sudo su command" or "sudo command"

if the former, its just sudo + command

Doesn't matter as the sudoers is corrupt, anything needing sudo or root rights is toast!

OMR

---

### Post by OldManRiver on 2009-04-28
> **bapoumba said:**
> To make it clear, do you get sudo problems with both the first user created when installing ubuntu and the second?

To boot in recovery mode, you need to do it at the grub menu, there is a line below your regular kernel line. If you do not see the menu, hit escape when booting.

Then:
```
adduser <username_here> admin
reboot
```

Ah someone understand, and good the "ESC" wilco, so see if I get in!!

Can not even use FireFox from the box as networking requires "root" rights when loading and with corrupted "sudoers" the networking will not set the IP address, so on backup box now.


OMR

---

### Post by OldManRiver on 2009-04-29
> **bapoumba said:**
> To make it clear, do you get sudo problems with both the first user created when installing ubuntu and the second?

To boot in recovery mode, you need to do it at the grub menu, there is a line below your regular kernel line. If you do not see the menu, hit escape when booting.

Then:
```
adduser <username_here> admin
reboot
```

B,

Thanks! that got me in. Set the admin users and reboot.  Had to run in recovery a couple time to clear hosed apps, but up now.

Still have a minor problem where FireFox only goes to Google an d I see IP on eth0 and localhost, but localhost not working either.

OMR

---

### Post by bapoumba on 2009-04-29
> **OldManRiver said:**
> B,

Thanks! that got me in. Set the admin users and reboot.  Had to run in recovery a couple time to clear hosed apps, but up now.

Still have a minor problem where FireFox only goes to Google an d I see IP on eth0 and localhost, but localhost not working either.

OMR
How do you get connected to the internet?

Please post the output to:
```
ifconfig
cat /etc/network/interfaces
cat /etc/resolv.conf

```

---

### Post by OldManRiver on 2009-04-30
B,

File of output uploaded.

OMR

---

### Post by OldManRiver on 2009-05-16
B,

Haven't heard back from you since I sent the file.  Also Internet gateway machine (Windows) went down and had to rebuild.  Can not get the D-Link wireless to install.  Misplaced the CD and none of the driver for this that are online work.  It is D-Link G520 V2B and only drivers from the CD work and even they were nested 3 levels deep on the CD.  Everyone that posts driver for this card post the top 2 levels and they wouldn't work this or install on "Autorun" and always had to hand install by drilling down in CD to find the right "Setup.exe" and then run.

If you have a source for these drivers as well, would be appreciated.  Can not very well test to see if all is running OK, if internet is down.

Thanks!

OMR

---

### Post by bapoumba on 2009-05-18
I'm sorry I did not answer. I saw your post, wanted to respond and it slipped away :/

Do you have a wired access to internet? From the files you uploaded, this is what I'm guessing. If so, are you using DHCP? In that case, you should add to the /etc/network/interface:

```
auto eth0
iface eth0 inet dhcp
```

You can add it just below "auto lo
/iface lo inet loopback"

Then save the file, and run:
```
sudo /etc/init.d/networking restart
```

For your wireless card, have you checked the restricted drivers (System > Administration > Hardware Drivers)?

---

### Post by OldManRiver on 2009-08-22
All,

Sorry did not log in for a while.

Yes I'm working all is resolved.

OMR

---

