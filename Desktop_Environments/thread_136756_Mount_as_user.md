---
title: "Mount as user"
date: 2006-02-26
forum: Desktop Environments
---

### Post by sameat on 2006-02-26
I have a script that dumps some files to a usb drive.  I haven't really figured out how to get handle the mounting of the drive.  I used to mount the drive as root before I ran the script, but I would like to include the mount command  in the script.

Is it possible to allow a user to mount and unmount drives?  How would I go about that?

Any other way to handle it?  The drive isn't always connected, so it's location (/dev/sd*) varies.

Thanks,
Sameat

---

### Post by ardchoille on 2006-02-26
You can put the mount command in the script and run the script as root.. that's what I do. You can even check for root privileges in the script before the script will do anything. You can do this by putting the following code in the script:
```

if [ $UID -ne 0 ];then
   echo "You do not have admin privileges to run this script."
   exit 1
fi

```
This will cause the script to check if the user has admin rights, run the script if the user has admin rights or exit the script if not. I use this in all my root scripts.

---

### Post by vbmaster on 2006-02-26
Easy, just edit the /etc/fstab and in the right partition, in the options section typer "user,"

just like this:

/dev/hdb1       /media/windows2  ntfs    user,nls=utf8,umask=0222 0       0

Stay cool ;)

---

### Post by sameat on 2006-02-26
Thanks for your comments.

For now, I will run the script as root.

I don't understand how I can use fstab to do this.

Let me explain...The drive typically ends up being assigned to /dev/sda1.  If I could count on that happening each time, this would be a no brainer.  

Sometimes, though, it gets assigned to a different place, for instance, if I have plugged in another usb device that grabs /dev/sda.  Also, it isn't always plugged in at boot.  Sometimes, even when it is plugged in, it doesn't get discovered at boot (same thing happens in other OS'es, so I'm guessing that's a hardware issue.)

Won't fstab choke if it isn't plugged in at boot?  And after boot, if I run mount -a and it's at another location, it won't work, will it?

Thanks for your help.

---

### Post by vbmaster on 2006-02-26
Oh... sorry then... 

But the boot doesn't matter... what matters is that the driver is not assigned always with the same name... and that refuses my tip...

But if it was assigned always with /dev/sda you would be able to mount it as user by editing the fstab as I said

Sorry... ;)

---

