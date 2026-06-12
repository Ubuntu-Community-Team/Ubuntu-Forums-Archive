---
title: "Mouting CD-ROM Drive"
date: 2005-03-11
forum: Desktop Environments
---

### Post by E-werd on 2005-03-11
Unable to mount the selected volume.
    mount: unknown filesystem type 'iso9660'

The above happens when I try to mount my CD-ROM drive.  I am totally stumped, what do I do?  :???: 

OS: Ubuntu Hoary Hedgehog 5.04 Preview

---

### Post by lorap on 2005-03-12
hi friend!
listen,i did have for a long time usb cdrom problems also and was getting the same message and after some other thing i've tried to do another ones.
now lets work.
if your cdrom doesn't appear when you open Computer----->Disks then all you've to do  is add a line in the file fstab.it's in /etc directory.
do it this way:
if it's external usb cdrom:
create a directory "usb-cdrom" in "/media" this way:

sudo mkdir /media/usb-cdrom

or if it's a regular one,internal cdrom the instead "usb-cdrom" choose simply "cdrom".

but remember all this you've to do if your cdrom doesn't appear.
next,to see it lets add something to the "fstab" file in "/etc" directory:

sudo nano /etc/fstab

this'll open "fstab".
now add this for an external usb cdrom:

/dev/sr0 /media/usb-cdrom udf,iso9660,ro(or "rw" if it can write),user,noauto 0 0

after what save the changes this way:press ctrl+o,to exit ctrl+x.

and if it's a regular one cdrom then:

/dev/hdc /media/cdrom udf,iso9660,ro(or "rw"),user,noauto, 0 0

now you're done.
hope i did help you friend.
have a nice day!
pavel

---

### Post by E-werd on 2005-03-12
I suppose I should have been a bit more specific.

Everything is showing up properly and my fstab is done properly. It is an internal CD-RW/DVD+-R drive.  It is at hdd.  Here is the line of my /etc/fstab:

```
/dev/hdd        /media/cdrom0   udf,iso9660 rw,user,noauto  0       0
```

Yes, it is hdd not hdd, I checked.  I was talking to a person I know that is quite excellent with Linux, and he said that perhaps iso9660 was not compiled into the kernel.  With this being said, I decided to, just for the sake of doing it, 'modprobe'ing iso9660; here are the results:

```

root@hockeybox:/home/ewerd # modprobe iso9660
FATAL: Error inserting isofs (/lib/modules/2.6.10-4-386/kernel/fs/isofs/isofs.ko): Invalid module format

```

I pasted that feedback to him and he said he had 3 words for me: "Something Is Broken"

What in the world does this feedback mean?

---

### Post by E-werd on 2005-03-12
Nevermind, I figured it out.  I was looking for the file that loads kernel modules at boot time, and I found /etc/modules.  I added iso9660 to that, as well as msdos (for floppies, wasn't able to read floppies either).  Everything works fine now.  :grin:

Thanks for trying to help, lorap.  I hope this thread might help anybody that has this problem in the future.

---

### Post by lorap on 2005-03-12
i really don't know what to say...
why wouldn't you just use /dev/hdc but not /dev/hdd?
pavel

---

