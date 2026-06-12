---
title: "Mounting my NTFS volumes in Ubuntu"
date: 2006-07-26
forum: Desktop Environments
---

### Post by mjpatey on 2006-07-26
Hello, group-

I'm trying to mount my main NTFS volume in Ubuntu, but am not sure where to go to do it.  When I go to System --> Administration --> Disks, one volume is labeled "disks-conf-hda1", and it's located in /dev/hda1.

When I navigate to /dev/hda1, it appears as an icon with an "x" in the upper-right corner, and won't open.  So I go back to "Disks" to see if there's any way to mount it from there.  I click "Browse" and get the message that I don't have permission to access it.

From here I'm not sure where to go to mount or be able to access the contents of the drive.

Any help you may have would be greatly aprpeciated!

-Mark

---

### Post by Ziox on 2006-07-26
ok let's try the command line: 

mkdir ~/hda1

sudo mount /dev/hda1 ~/hda1

i think that's the command to mount that volume, but if there are errors post back.

---

### Post by mjpatey on 2006-07-26
Oh boy, I did a bad thing... while poking around in "Disks" I found a partition that was showing as unformatted.  So I just formatted it as VFAT (so it could be shared between Ubuntu and Windows).

For the path, I selected /home (as /boot was selected by default, and I didn't want it to show there, but rather in my home directory).

It took less than a second to "format" the partition, and now anything I try to access anywhere is... gone.

I click on the Terminal, it says directory not found... same with EVERYTHING.  Anything I try to do returns the same message.

Did I unwittingly delete my /home directory?  It sure looks like I did.  Is there some way to repair this, or should I cut my losses and reinstall?

-Mark

---

### Post by mjpatey on 2006-07-26
OK, strangely enough (to me, anyway!) a reboot fixed the problem I had described in the post above.  Phew!

About to try the command line instructions.  Thanks, Ziox!  I'll let you know how it goes.

-Mark

---

### Post by mjpatey on 2006-07-26
Ziox-

It says...

mount: /dev/hda1 already mounted or /home/[myname]/hda1 busy
mount: according to mtab, /dev/hda1 is mounted on /tmp/disks-conf-hda1

So it's mounted in a temp folder, I guess?

-Mark

---

### Post by endfx on 2006-07-26
Yeah, it looks like its mounted.

just do a 
>$ cd /home/[myname]/hda1
and there is your mounted drive

Or you could:
>$ sudo umount /dev/hda1
>$ sudo mkdir /media/hda1 ; mount /dev/hda1 /media/hda1

and now it will be mounted to /media/hda1

---

### Post by endfx on 2006-07-26
sorry, ignore the "cd /home/[myname]/hda1" part. Its not mounted there.

also if you are ever confused of where things are mounted or if they are mounted just type:

mount

that lists all devices and where they are mounted.

---

### Post by mjpatey on 2006-07-26
I'm having a hard time with this.  When I type "mount", it says:

/dev/hdb3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hda1 on /tmp/disks-conf-hda1 type ntfs (rw)

... the last one is hda1, which I'm interested in.  How do I save to it?  Do I save to the path /dev/hda1, or /tmp/disks-conf-hda1 ?

Is there some nickname I can give it, and have it show up next to my other volumes, say on the desktop?

-Mark

---

### Post by Ziox on 2006-07-26
> **mjpatey said:**
> I'm having a hard time with this.  When I type "mount", it says:

/dev/hdb3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hda1 on /tmp/disks-conf-hda1 type ntfs (rw)

... the last one is hda1, which I'm interested in.  How do I save to it?  Do I save to the path /dev/hda1, or /tmp/disks-conf-hda1 ?

Is there some nickname I can give it, and have it show up next to my other volumes, say on the desktop?

-Mark

if you are saving a file to it, then you have to save it to /tmp/disks-conf-hda1.

But you can mount that drive to anything you want: for example:

umount /dev/hda1 /tmp/disks-conf-hda1
then:

mkdir ~/Desktop/hda1

then:

mount /dev/hda1 ~/Desktop/hda1

this method would allow you to acces that drive through the folder /home/yourname/Desktop/hda1

Note: if those commands doesn't work, add sudo to the front of them

---

### Post by MotK on 2006-07-26
try this: (i hope this is what you're looking for...it helped me)

[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)


i then just dragged the icon onto my desktop so i can read my windows stuff...

---

### Post by endfx on 2006-07-26
Just for your information,

The /dev/hda1 is just a file that represents your harddrive device.
It isn't written to or read from or navigated to. You need to mount a device to a directory, and then you can navigate, read, and write to the harddrive.

So if you want to read something, navigate to /tmp/disks-conf-hda1
and save your file there.

Also note, that this seems like a strange place to mount a hard drive. I'm not sure why it was mounted there.

I would:
sudo umount /dev/hda1
sudo mkdir /media/hda1
mount /dev/hda1 /media/hda1

This just seems like a more logical place to mount your harddrive.

Does this make sense?

---

### Post by mejohnsn on 2006-07-26
Hi, endfx-

I realize you are trying to be helpful, but did you actually try these commands before posting them? I tried them, and I get the error message, "mount: only root can do that" on your third line.

And even if I _do_ prepend 'sudo', I get a _very_ strange filesystem! I have to be root just to do 'ls', and even with sudo, bash does not recognize 'cd'!!

Also, although 'mount' reports this as a '(rw)' filesystem, it is really read-only.

So yes, the mount-point you suggest is more logical, but there is still something missing; the instructions you give still do not yield a useful NTFS filesystem mount-point.

OTOH, if the OP could be content with read-only access to the NTFS filesystem, he could follow the instruction at [http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

i.e., add the "-t ntfs" to specify the filetype, and "-o nls=utf8,umask=0222" to specify character coding and user-permissions.

This will yield a mount-point that is fully functional, although still read-only.

---

### Post by mjpatey on 2006-07-26
Thanks, everyone!  It worked like a charm.

-Mark

---

### Post by endfx on 2006-07-31
Sorry, I guess I should have clarified some things:

The commands I gave assumed all the options, permissions were setup in /etc/fstab. I assumed /etc/fstab was setup because hda1 seemed to be automatically mounted when you started your computer.

---

### Post by mjpatey on 2006-07-31
endfx-

It worked fine for me.  I'm not sure how mejohnson's system is configured, but all's well here.

Thanks!

-Mark

---

