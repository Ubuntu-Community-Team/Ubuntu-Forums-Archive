---
title: "Automatic copy of files to CD/DVD"
date: 2011-11-16
forum: Desktop Environments
---

### Post by thebulk on 2011-11-16
Hi everyone.

I have search the net several times to find a solution to this but have not come across anything as yet so thought I would come as you guys for some advice or thoughts.

I have recently created a back-up server where it backs up 3 windows machines to one xubuntu based Linux machine. This all works well and creates the back-ups nicely. It does everything I need except one feature.

I need the Snapshots created to be backed up to a removable  device such as CD or USB Key. I am looking to use CD/DVD as it would be easier for the person I am setting this system up for. Here are the features I am looking for:

Insert the CD/DVD (one for each day of the week except Saturday and Sunday)
Then at a specified time say 10pm GMT selected folders are burned to the DVD automatically without input from the user.

It would also need to be able everything from the parent folder incase new files are backed up after the last back to CD.

If any one has any thoughts or suggestions to make about this please post them here or send me a PM. Either is fine by me.

And thanks for your help in advance everyone. I could probably work this out but I am having a 'writers block' at the moment and nothing seems to make sense at the moment in regard to this back up of a back up system.

Cheers

---

### Post by cchester on 2011-11-16
I am not positive but it seems like it could be done with the default backup program in Ubuntu as long as the cd/dvd/usb is either in the drive or plugged into the computer but I maybe wrong.

---

### Post by BobMarleyy on 2011-11-17
> **thebulk said:**
> 
Insert the CD/DVD (one for each day of the week except Saturday and Sunday)
Then at a specified time say 10pm GMT selected folders are burned to the DVD automatically without input from the user.


Recently I stumbled upon something called cron:
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

This lets you run some program(s) at specified times. The next step would assign a program that creates this backup, as chester suggested:
> **cchester said:**
> I am not positive but it seems like it could be done with the default backup program in Ubuntu as long as the cd/dvd/usb is either in the drive or plugged into the computer but I maybe wrong.

I think this back-up tool works, but you can use any burning program you like, e.g. brasero, xfburn (xfburn -i /path/to/image), etc. Just try some of them, and use the burning program you like.

I hope this helps you.
Cheers,
Bob

---

### Post by thebulk on 2011-11-17
That sounds like a good idea to me. I will look into it to see if I can get something together to do what I want. I was thinking of using USB drives but then I thought about the issue of safe ejection of the USB drive as the server once installed will be run without monitor so they need to be able to do something that does not require user interaction.

Would it be possible for cron to safely eject the USB once the back up is complete otherwise I will look into the cron job running the normal ubuntu back-up tool.

Thanks again guys for your help, I really do appriciate it.

---

### Post by BobMarleyy on 2011-11-18
I can think of two options to solve this.

Copying to an USB might make it easier for you. Try something like this:
```
mount /media/usbdevice1 && cp -ru /stuff/to/backup /media/usbdevice1 && umount /media/usbdevice1
```
Where cp -ru means copy (cp) folder (-r) and updated/new files only (-u). Note that && requires the first command to be finished, before the second command is run, so first the device is mounted and only when mounted, the copy command is run.

Using cron you can run this whenever you want. However, to use these mount options your usb device should be specified in fstab, for more information see:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
For example add this line to your fstab:```
/dev/sdc1  /media/usbdevice1  vfat  user,noauto,exec  0  0
```
To understand why this line should look like this, check the website. Anyway, the /media/usbdevice1 should be created in advance (sudo mkdir /media/usbdevice1) and the combination of the options, user and noauto, allows you to safely remove the usb device without requiring root privileges. Specifying the device with UUID might work better than /dev/sdc1, because UUID is constant and /dev/sd*1 is not.

An alternative to use fstab, would be using a command with root privileges to remove you usb device. Again this can be done with cron, just add it to the root user ("Commands that normally run with administrative privileges (i.e. they are generally run using sudo) should be added to the root user's crontab (instead of the user's crontab):"). This requires you to insert the usb, then it would be automounted (unless otherwise specified in fstab), just issue the copy command (cp /this/stuff /to/this/device) and then you can unmount using:```
sudo umount /media/usbdevice1
``` Be sure to check the name of your usbdevice, since this determines where it is mounted. To check what is mounted, you can simply type mount in a terminal.

I would prefer the first method, because it is more specific in what devices should be mounted/unmounted and because the cron job does not require root privileges.

Let me know of this is useful in your quest :p
Bob

---

