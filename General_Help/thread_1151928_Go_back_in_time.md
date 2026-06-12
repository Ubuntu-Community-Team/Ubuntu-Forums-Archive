---
title: "Go back in time"
date: 2009-05-07
forum: General Help
---

### Post by Egi_Power on 2009-05-07
Hi all!

First things first, I'm using Ubuntu 8.04, Hardy.
Today I updated my system through Synaptic.
The following updates were applied:

> Commit Log for Thu May  7 15:01:53 2009


Upgraded the following packages:
libwmf0.2-7 (0.2.8.4-6) to 0.2.8.4-6ubuntu0.8.04.1
linux-generic (2.6.24.23.25) to 2.6.24.24.26
linux-headers-generic (2.6.24.23.25) to 2.6.24.24.26
linux-image-generic (2.6.24.23.25) to 2.6.24.24.26
linux-restricted-modules-common (2.6.24.16-23.56) to 2.6.24.17-24.1
linux-restricted-modules-generic (2.6.24.23.25) to 2.6.24.24.26
nvidia-glx-new (169.12+2.6.24.16-23.56) to 169.12+2.6.24.17-24.1

Installed the following packages:
linux-headers-2.6.24-24 (2.6.24-24.53)
linux-headers-2.6.24-24-generic (2.6.24-24.53)
linux-image-2.6.24-24-generic (2.6.24-24.53)
linux-restricted-modules-2.6.24-24-generic (2.6.24.17-24.1)
linux-ubuntu-modules-2.6.24-24-generic (2.6.24-24.39)
My question is:
Is it possible to undo these changes?

During the update I had to choose what to do with the /boot/grub/menu.lst file. I choose keep it as is (or something similar - that was the default option). Now I can't boot into the new kernel, still using 2.6.24-23.

> Linux ***-desktop 2.6.24-23-generic #1 SMP Wed Apr 1 21:47:28 UTC 2009 i686 GNU/Linux

Or is there an easier way to fix my menu.lst file, so I could use the latest kernel?

Thank you in advance.

Egi_Power

---

### Post by fabertawe on 2009-05-07
You should accept the new menu.lst when offered. It's rather confusing as it doesn't actually replace yours with a new one but updates it, which is what we want!

For now try this...
```
sudo update-grub
```

You may still have to go in and edit menu.lst manually if it doesn't update the default booted kernel, i.e. change it to the latest.

---

### Post by Egi_Power on 2009-05-07
Thank you for your quick answer.

Your advice gave me the following output:

```
***@***-desktop:~$ sudo update-grub
[sudo] password for ***: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-24-generic
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```

As I can see, it founds the new kernel, 2.6.24-24, but the menu.lst file is still the same.

> ## ## End Default Options ##

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=9fe7ad52-ad78-40f3-b6de-e19d8b084c93 ro quiet
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=9fe7ad52-ad78-40f3-b6de-e19d8b084c93 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9fe7ad52-ad78-40f3-b6de-e19d8b084c93 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9fe7ad52-ad78-40f3-b6de-e19d8b084c93 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 7 BETA
# title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

I even tried to reinstall all the above mentioned packages (related to the kernel), so maybe I would get the same popup (it was deb config or something like that) and I could choose another option, but this time it didn't ask about menu.lst.
I didn't accept the new menu.lst before because they were named very confusingly. :(

Any other ideas?

Thx.

Egi_Power

---

### Post by fabertawe on 2009-05-07
Hmn... ok... the obvious thing to try now is removing (renaming) your current menu.lst and let it rebuild it from scratch...
```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst-backup
sudo update-grub
```
Fingers crossed that'll fix it!

---

### Post by Egi_Power on 2009-05-08
Thank you for your reply.

The following commands created the new menu.lst for me, just as you said:
```
***@***-desktop:~$ sudo mv /boot/grub/menu.lst /boot/grub/menu.lstbackup
[sudo] password for ***: 
***@***-desktop:~$ sudo update-grub 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-24-generic
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```

It might be even better, because now I have hidden menu, which I can access by pressing ESC. The only thing is now there is only 3 seconds if I want to enter the GRUB menu, but that I can fix by editing the menu.lst.

> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		***3***

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

There is another thing, it missed my *NOT LINUX* partition, the file ended like this:
> title		Ubuntu 8.04.2, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Then I just took the last few lines from the backup file, and it seems to work.> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 7 BETA
# title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
I already booted in the other system as well.

Now there is only one thing left, remove the 2.6.24-19 kernel. What's the easiest and simplest way to do it?

Thank you for your really quick help.
I appreciate it very much.
Take care.

Egi_Power

---

### Post by fabertawe on 2009-05-08
Glad it worked for you :)

The easiest way to remove old kernels would be to go into Synaptic Package Manger (System->Administration menu) and type 2.6.24-19 into the search box ("name" only). Then "mark for complete removal". Your menu.lst will be rebuilt without that kernel. It will also leave everything after "### END DEBIAN AUTOMAGIC KERNELS LIST" untouched, so you will not have to enter your Windows entry again.

The only thing I would add about having the menu hidden is to make sure the following entry in menu.lst is set to "false"...
```
## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false
```
and
```
default         0
```
...otherwise when you add a new kernel it will change the default kernel in menu.lst to the previous one and not the newly installed kernel. Hope that makes sense!

---

### Post by Egi_Power on 2009-05-08
Hi!

The stuff after "*### END DEBIAN AUTOMAGIC KERNELS LIST*" disappeared when we rebuilt the menu.lst from scratch. I just had to copy it that time.

> The only thing I would add about having the menu hidden is to make sure the following entry in menu.lst is set to "false"...
Code:

## should update-grub adjust the value of the default booted system
## can be true or false
**[COLOR="Blue"]#[/COLOR]** updatedefaultentry=false

If I understand the syntax of menu.lst file, then this entry should not make any difference if it's true or false, because it is commented out. If we would remove the # symbol, then it would make a difference.

The second part matched your recommendation.
> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

About removing the old kernel.
The search for 2.6.24-19 returns a lot of hits (even though only the NAME is selected), but only 3 packages installed.
I found the following:
*linux-image-2.6.24-19-generic*
I just ***Mark for Removal*** and it tells me that I'll have to remove *linux-restricted-modules-2.6.24-19-generic* and *linux-ubuntu-modules-2.6.24-19-generic* also.
I'm gonna try to remove them and see what happens.
Fingers crossed!

Thanks again for your posts, you are being really helpful.

Best regards,

Egi_Power

---

### Post by fabertawe on 2009-05-08
Hi Egi_Power,

> **Egi_Power said:**
> Hi!

The stuff after "*### END DEBIAN AUTOMAGIC KERNELS LIST*" disappeared when we rebuilt the menu.lst from scratch. I just had to copy it that time.

Yes, that's correct. Because we renamed the file so it didn't exist and was recreated. Now that it's there again update-grub will re-use it and not touch anything after that line. So you wont have to edit it to put it back in again.

> If I understand the syntax of menu.lst file, then this entry should not make any difference if it's true or false, because it is commented out. If we would remove the # symbol, then it would make a difference.

Yes and no!. A double ## is a comment in the "AUTOMAGIC KERNELS LIST" section. The line beginning with a single # is in fact used. Outside of that a single # is a comment!

> About removing the old kernel.
The search for 2.6.24-19 returns a lot of hits (even though only the NAME is selected), but only 3 packages installed.
I found the following:
*linux-image-2.6.24-19-generic*
I just ***Mark for Removal*** and it tells me that I'll have to remove *linux-restricted-modules-2.6.24-19-generic* and *linux-ubuntu-modules-2.6.24-19-generic* also.
I'm gonna try to remove them and see what happens.
Fingers crossed!

That is what should happen, it's safe to go ahead :)

> Thanks again for your posts, you are being really helpful.

Best regards,

Egi_Power

You're welcome, glad I could be of assistance.

---

### Post by Egi_Power on 2009-05-08
Hi!

> The line beginning with a single # is in fact used.
My old menu.lst looked like this (it's in menu.lstbackup now):
> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
I had the GRUB menu without pressing ***ESC***.

My new menu.lst lookes like this:
> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
Now I have to press ESC if I want to get to the boot menu.
That's why I think the lines start with ***#*** are commented out.

> Outside of that a single # is a comment!
What did you mean by that?

I have to go to work.

Take it easy.

Egi_Power

---

### Post by fabertawe on 2009-05-08
Ok... there's a section which starts with
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
```
and ends with
```
## ## End Default Options ##
```
Inside that section quotes start with ##
Before and after that section quotes start with #

Hope that's clear :)

---

### Post by Egi_Power on 2009-05-09
Hi!

I looked into the menu.lst file, and now I see what you meant about # and ##.

Anyway, I'm glad we fixed my original issue with the GRUB menu update.

Thank you again.

Best regards,

Egi_Power

---

### Post by fabertawe on 2009-05-09
You're welcome. Don't forget to mark the thread as solved :)

---

### Post by Egi_Power on 2009-05-09
> **fabertawe said:**
> You're welcome. Don't forget to mark the thread as solved :)

There is no such a feature on these forums at this time.
[http://ubuntuforums.org/showthread.php?t=1044714]("http://ubuntuforums.org/showthread.php?t=1044714")

Best regards,

Egi_Power

---

