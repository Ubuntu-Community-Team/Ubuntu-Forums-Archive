---
title: "Desktop graphic gone after installed updates"
date: 2012-01-22
forum: Desktop Environments
---

### Post by UltimateCat on 2012-01-22
Hi:)
After installing updates yesterday my gnome desktop doesn't look the same.  It has a long black rectangular box behind my cairo dock and it's in the way of being able to read my web page that's up as well. Also; my screen saver vanished and the screen is black.

I went to System> Admin> Ati Catalyst Control Center and was given this message:

"There was a problem initializing Catalyst Control Center; No ATI graphics driver is installed or
the ATI driver is not functioning properly"
Is this a driver issue?

I went to:
help.ubuntu.com/community/RadeonDriver

I checked on my card: ATI Technologies Inc
and saw Radeon 3100

Not sure what is going on any advice would be appreciated;)
Very confused here; What can I do?

---

### Post by UltimateCat on 2012-01-25
I've tried:
```
aticonfig --initial

```
That command gave me :
```
Could not find configuration file, so create an empty one.  Failed to create empty configuration file

```
I rebooted and than tried the Catalyst Control Center and still got this message
" No ATI driver is installed or ATI driver is not functioning properly"
Someone; please enlighten me

---

### Post by inobe on 2012-01-25
don't know much about ati drivers, if it were me, i would go to hardware drivers to see if it's active, if yes, disable it, restart and enable, assuming that's how you installed it.

not sure if that will work, may cause more issues, create a backup plan!

research how to manually install ati drivers, or even start consider selecting a previous kernel version from the ubuntu grub menu, assuming it was a kernel update that caused this.

note: if you manually installed the ati driver and that update was a new kernel, you will need to install your ati driver again, this affect will not happen if done from additional drivers.

you may want to include exactly what got updated/ updates on next post.

---

### Post by UltimateCat on 2012-01-27
inobe:
Thank you for good advice.
It was a update to my kernel.
The version I had was 2.6.32 - 25 and the update bumped the kernel to 2.6. 32 - 38

You said to post and include what got updated....I don't know how to do that however I know that the update was huge like: 823.7MB

I checked on the driver and Ubuntu told me that it is in use and working properly.
So I am going to try to disable it reboot and then inable it.

Of course I will research it (ati driver) first because I don't want any more issues as my U.E. 2.7 and all it's graphic's are gone.

How could I find all that was updated so I can post it?

---

