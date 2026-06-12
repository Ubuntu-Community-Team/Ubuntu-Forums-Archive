---
title: "Write access to disk"
date: 2006-07-01
forum: Desktop Environments
---

### Post by tellnes on 2006-07-01
Hello Ubuntuers, 

I have a 200gb USB disk, formated with NTFS, attached to my dapper box, and i would like write access to it.
I have searched this forum, and tried alot and are close to a solution i think, anyhow, some strange behavior needs to be solved.

What i have done:
I went to this site and followed the proccedure there: [http://www.jankratochvil.net/project/captive/]("http://www.jankratochvil.net/project/captive/")

My fstab line for the usb disk looks like this: 
/dev/sda1       /media/usbdisk  captive-ntfs defaults,noauto 0 0

I have made i folder in /media called usbdisk, and done a mount to that folder in the console for the usbdisk. I have also addes myself and root to the captive group.

If i log in as root, i can browse to the usbdisk folder, read and write to the usb disk, i can however not change permissions on the dir or folders, so captive kind of works for the root user.

As myself, i cant even view the content of the usb folder, it maps a usbdisk called "temp/disk-conf-sda1" on my desktop, but i cant access it due to permissions it says.

is there anyone who have got this to work completly? it works as root, not as myself, even though im in the root group, and captive group..and whats with the temp usb icon it comes up with..?

regards

ole j

---

### Post by grooverider on 2006-07-01
try 'sudo chown -R user:group /path/to/mounted-device'
and possibly
'sudo chmod -R 777 /path/to/monted-device'
maybe that will help... good luck

---

