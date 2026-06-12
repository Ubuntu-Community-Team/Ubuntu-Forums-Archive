---
title: "Cannot hibernate or standby"
date: 2008-12-10
forum: General Help
---

### Post by thedonpsx on 2008-12-10
Whenever I select the hibernate or standby option in Intrepid, all that happens is the screen blacks out with a the small flashing cursor in the top left (like when your running from the prompt), when the power button or any key is pressed, nothing happens, and the only way to get back is to reboot the system. Anybody have any ideas?

---

### Post by ubuser_7 on 2008-12-10
What machine are you using? 

I had similar problems on my thinkpad, and it was solved by a couple of simple fixes. 

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61#Suspend_with_Nv140m](http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61#Suspend_with_Nv140m)

The above link is for 8.04 on T61, because Intrepid works out of the box on my Thinkpad. I am guessing you *might* need something similar.

---

### Post by scholzilla on 2008-12-10
I'm having the same problem as ubuser_7. I'm not sure if the post linked in the response is germane to my problem. I'm now using intrepid and my system runs w/ Phoenix BIOS (not the same BIOS in the post). Any help appreciated.

---

### Post by giacomo on 2008-12-12
I've the same problem. If I logout hibernating, my Ubuntu is unable to restore the session.
Can I post something to help you help me?

Output from:
```
uname -a
```
is:
```

Linux MyHostName 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux

```

Another thing: when I activate the hibernate command the system says that I not have a swap partition or that this swap partition is not activated. Obviously this is false. (Or I don't understand what the system wants!).

Thanks in advance,
Bye!

---

### Post by giacomo on 2008-12-16
Oopss... Really the system was correct the swap partition UUID in /etc/fstab was wrong. This maybe caused upgrading from ubuntu 7 to 8 (I think...).

With this command, anyone can read a partition UUID (my swap was /dev/sda2):

```
sudo vol_id -u /dev/sda2
```

Then copy/paste the code in /etc/fstab and

```
sudo swapon -a
```

(Last command is needed only for the current session, next time you restart the system swap will be active.)

Anyway, hibernation still not work!

Bye...

---

### Post by PocketDog on 2008-12-16
To make sure your UUID entries all match (hibernating won't work if they don't) make sure you have initramfs-tools ```
sudo apt-get install initramfs-tools
``` check your swap partition's UUID ```
sudo blkid
``` and verify that it's the same in your fstab ```
gksudo gedit /etc/fstab
``` It's also necessary to make resume point to the correct UUID ```
gksudo gedit /etc/initramfs-tools/conf.d/resume
``` and then update everything ```
sudo update-initramfs -u
``` and lastly, reboot. Everything should be sweet.

---

### Post by PocketDog on 2008-12-16
Oh, by the way; your swap partition has to be at least as big as your total RAM or hibernate can't work

---

