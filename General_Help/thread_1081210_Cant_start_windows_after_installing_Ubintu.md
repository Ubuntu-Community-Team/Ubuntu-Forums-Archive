---
title: "Cant start windows after installing Ubintu"
date: 2009-02-26
forum: General Help
---

### Post by Andrewz09 on 2009-02-26
Hello
I recently download and installed Ubuntu
so now i have a partition with Windows Vista
and a partition with Ubuntu
but when i restart it automaticly loads Ubuntu
when i press "Del" on boot, it shows only:
Ubuntu
Ubuntu - Safe Mode
Memtest

No windows...
help >_<

---

### Post by Steve H on 2009-02-26
Have you made sure the windows partition is still there and on the first partition on the first disk? If so you need to edit your config file for GRUB (the OS loader)

```
gksudo gedit /boot/grub/menu.lst
```

Change this:

```
hiddenmenu
```

to this:

```
#hiddenmenu
```

Add windows entry to bottom:
```

title Windows XP
root (hd0,1)
makeactive
chainloader +1
```

---

### Post by Andrewz09 on 2009-02-26
Where do i enter the last part?

title Windows XP
root (hd0,1)
makeactive
chainloader +1

like after what line?
below what line?

---

### Post by shadowhacker on 2009-02-26
Add it to the very bottom of the file.

---

### Post by stim on 2009-02-26
You would want to post this at the very bottom of the grub file.  It's assuming your Vista partition is in a specific place: his is (hd0,2) mine is (hd0,1). You will need to know where your windows partition is.  Mine looks like this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

---

### Post by Andrewz09 on 2009-02-26
> **stim said:**
> You would want to post this at the very bottom of the grub file.  It's assuming your Vista partition is in a specific place: his is (hd0,2) mine is (hd0,1). You will need to know where your windows partition is.  Mine looks like this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

Ok done so
Now i have the Windows boot option
BUT when im pressing it is says:
"BootMGR is missing"
"Press Alt + Ctrl + Del to restart"

now just in case we need it, my windows is on the "disk-1" partition.

---

### Post by stim on 2009-02-26
I *think* you would want (hd0,1) in that case. Try that out and report back.

---

### Post by Andrewz09 on 2009-02-26
And here is an image of how i done it
tell me if its ok
[http://img150.imageshack.us/img150/2929/333cnf.jpg]("http://img150.imageshack.us/img150/2929/333cnf.jpg")

---

### Post by Andrewz09 on 2009-02-26
> **stim said:**
> I *think* you would want (hd0,1) in that case. Try that out and report back.
It is already set to that one, same problem..

---

### Post by shadowhacker on 2009-02-26
You need to use gparted to find out exactly which partition it is. It's under System > Administration > Partition Editor. If it's not there, open a terminal and type:
```
sudo apt-get install gparted
```
Once you open gparted, you should see the ntfs partition. It will say something like /dev/sda2 or something. Subtract 1 from this number to get the partition number for grub. (/dev/sda2 = (hd0,1))

---

### Post by Andrewz09 on 2009-02-26
Right so i chacked parition managere
and it says that the windows partition is hd0,3
i done what you said about modifing the boot
and set it to hd0,2 (as you guys said)
So now when i boot the windows (from the menu) it says:
A disk read error occured

---

### Post by shadowhacker on 2009-02-26
It sounds to me like something got messed up during partition resizing. I would throw in your windows cd, run the recovery console, and use fixboot and fixmbr.

You will then only be able to boot windows, let me know when you get to this point and I will tell you how to fix grub.

---

### Post by Steve H on 2009-02-26
Cheers for taking over Shadowhacker, I got sidetracked, just come back and noticed the saga of replies.

---

### Post by shadowhacker on 2009-02-26
Not a problem Steve H. I do however have to go work on a chebby. I'm sure help is abundant in case I'm not back in time :)

---

### Post by Andrewz09 on 2009-02-26
Here is an Update:
After a failure of the system restore
my HDD went threw near death expiriance
which resulted at first in a total boot failure
and ended in the lose of all my partitions, 
including 80GBs of data lose.
After many attepts to Format and reinstall windows
i managed to do so only with the windows XP installetion disk.
so now im on a clear HDD with 2 new partitions and Win XP.
Bye bye 80GBs of my favorite movies, games, important software and music.
Even though i dont blame Ubuntu in this disaster
i dont think ill try Linux no more.
thank you all for the support
ill stay here for a while to see what you have to say.

---

### Post by OneShirtChris on 2009-02-26
for a little more foolproof installation of ubuntu try a wubi installation. boot into windows and then place the livecd into the drive. ubuntu will install like a program and set up the grub for you. No messing around with partitions required! [http://wubi-installer.org/faq.php]("http://wubi-installer.org/faq.php")

---

