---
title: "How can i stop daul booting to windows and just boot to ubuntu?"
date: 2009-04-03
forum: General Help
---

### Post by krine11 on 2009-04-03
Hi, I have tried ubuntu for a while now and its getting really annoying for useing it all the time but always slecting it for boot and my brothers who are not such pros at computers cant do it either so i just want to remove windows and keep ubuntu my os for my computer all the time. Can you tell me some steps for doing this? Please, it will be very nice if you guys do i mean i LOVE ubuntu and it is SOO faster than windows xp.

BTW i have Windows XP Media center (But its just a 30 day trial one..)

---

### Post by albinootje on 2009-04-03
> **krine11 said:**
> i just want to remove windows and keep ubuntu my os for my computer all the time. 

If you want a GUI solution, then install "startupmanager", and use that to remove MS-Windows from the boot menu to start with.
After installation it's in ->System ->Administration ->Startupmanager

---

### Post by Monotoko on 2009-04-03
Open partition Manager (Install GParted if you dont have it)
and delete the windows partition.

Then also delete the Microsoft Windows entry from /boot/grub/menu.lst

sorted :)

For any needs of Windows that may come up in the future (and they will) you may need to use virtualization software, search for virtualbox for more info

---

### Post by krine11 on 2009-04-03
Can the 2nd post post a bit clear? still confused on that

---

### Post by albinootje on 2009-04-03
Try this in a terminal :
```

sudo apt-get install gparted
gksudo gparted

```
Make sure the Windows partition is not mounted.

Then remove the Windows partition from the boot menu as following :
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst

```
And remove the section for Windows, which is probably all the way at the bottom of that text file.
After that save it, and reboot to test it.

---

