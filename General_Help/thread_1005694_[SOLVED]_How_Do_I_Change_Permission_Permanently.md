---
title: "[SOLVED] How Do I Change Permission Permanently ?"
date: 2008-12-08
forum: General Help
---

### Post by Rodney9 on 2008-12-08
Hello, When I use this code  - 
> sudo chown rodney /dev/rtc0
to change it's permission, it only lasts a day or to the next full reboot .
How do I make it permanent ?

Rodney.

---

### Post by Afkpuz on 2008-12-08
```
sudo chown rodney:rodney /dev/rtc0 
```

Then, go into a file browser and right click on rtc0.  Click on the permissions tab and change the read and write priveleges there.  If they are reset again, then it's some internal setting within ubuntu which defaults permissions in /dev/

---

### Post by soro2005 on 2008-12-08
The owner is being set when the device is created by the rtc driver/kernel module. To change it permanently, you would probably have to find the config files of the kernel module and tinker with them. I doubt, though, that that's a very good idea, and I'm almost certain that there is a less system-threatening way of achieving whatever it is you want to eventually achieve by taking over ownership. So perhaps you could briefly explain why you don't want root to own /dev/rtc0

---

### Post by snova on 2008-12-08
It isn't a real file, so it doesn't have stored permissions on disk. You'd have to add a boot script to do it again every time you turn the computer on.

But why would you want to?

---

### Post by Rodney9 on 2008-12-09
> **snova said:**
> It isn't a real file, so it doesn't have stored permissions on disk. You'd have to add a boot script to do it again every time you turn the computer on.

But why would you want to?

I want the computer to wake every morning at the time I set.
I use  > rtcwake -u -s 32400 -m on in 'Alarm Clock' to wake the PC from hibernate 9 hours after.
If I don't have permission it fails to run and the PC does not start.
What script would I need run to set this or change the permission everyday ?

Rodney.

---

### Post by 3rdalbum on 2008-12-09
Add the command to the file "/etc/rc.local" and it will be executed every time you boot up. Make sure it is added before the "exit" line.

---

### Post by jocko on 2008-12-09
> **Rodney9 said:**
> I want the computer to wake every morning at the time I set.
I use   in 'Alarm Clock' to wake the PC from hibernate 9 hours after.
If I don't have permission it fails to run and the PC does not start.
What script would I need run to set this or change the permission everyday ?

Rodney.
Wouldn't it work the same if you just put sudo in front of the comand:
```
sudo rtcwake -u -s 32400 -m on
```?

---

### Post by geirha on 2008-12-09
Hm. On Hardy there's only /dev/rtc, and it is readable and writeable to the root user and the audio group. On Intrepid it's readable and writeable to the root user and the root group, and /dev/rtc is a symlink to /dev/rtc0 instead.

The same permission rule for udev remains though, setting audio as the group, but since /dev/rtc now is a symlink, I'm guessing it just doesn't get applied. You can edit /etc/udev/rules.d/40-permissions.rules
```
sudoedit /etc/udev/rules.d/40-permissions.rules
```
find the line:
```
KERNEL=="rtc",              GROUP="audio"
```
And add a new line directly underneath it, for rtc0:
```
KERNEL=="rtc0",             GROUP="audio"
```

Then restart udev with ```
sudo /etc/init.d/udev restart
``` After that, if you are a member of the audio group, you should be able to read and write to the device. And the change should be permanent.

---

### Post by Rodney9 on 2008-12-11
> **geirha said:**
> Hm. On Hardy there's only /dev/rtc, and it is readable and writeable to the root user and the audio group. On Intrepid it's readable and writeable to the root user and the root group, and /dev/rtc is a symlink to /dev/rtc0 instead.

The same permission rule for udev remains though, setting audio as the group, but since /dev/rtc now is a symlink, I'm guessing it just doesn't get applied. You can edit /etc/udev/rules.d/40-permissions.rules
```
sudoedit /etc/udev/rules.d/40-permissions.rules
```
find the line:
```
KERNEL=="rtc",              GROUP="audio"
```
And add a new line directly underneath it, for rtc0:
```
KERNEL=="rtc0",             GROUP="audio"
```

Then restart udev with ```
sudo /etc/init.d/udev restart
``` After that, if you are a member of the audio group, you should be able to read and write to the device. And the change should be permanent.

Thank You

---

