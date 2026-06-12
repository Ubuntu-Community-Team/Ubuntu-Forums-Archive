---
title: "Can I use nautilus to look at files on my camera?"
date: 2006-08-23
forum: Desktop Environments
---

### Post by aleska on 2006-08-23
I just tried attaching my camera, by USB to Ubuntu, and was very pleased that it detected it, and offered me the option to import.  I like using F-Spot, so I changed the preferences in "removeable drives and media" to use F-Spot instead of gthumb to import.  In case anyone is interested in how to do this, you simply change the command from "gnome-volume-manager-gthumb %h" to "/usr/bin/f-spot-import %h".
Anyway, so far so good, imports photos just fine.  Problem is that F-Spot, once it imports, didn't give an option to delete the files from the camera.
So, I thought I'd find them and manually delete through nautilus.  That's when I realized, after lots and lots of searching, I have no idea how or where to find my attached camera.  
Does it automount?  Where can I find it so I can delete (note: I don't want to have to delete picture by picture on the camera...I want to use my computer to do it).
Any suggestions?
TIA

---

### Post by orb9220 on 2006-08-23
I think usb devices or in media/sda look in your media folder. Be sure you run a gksudo nautilus if you can't delete with a regular nautilus.

---

### Post by aleska on 2006-08-23
I thought that's where it might be too.  But under /media are only /media/cdrom & /media/cdrom0
Any other suggestions on where to look?

---

### Post by aleska on 2006-08-23
Note, when I enter the command "mount" before and after connecting the camera, the list of mounted devices is the same.  So, nothing mounts it on the fly per se...I think anyway.

When I type "lsusb", I get
Bus 001 Device 010: ID 04a9:311b Canon, Inc.
among other things.  But I don't know how to use this info to actually access files on it to copy or delete.

Again, anybody have any ideas?    
Thanks!

---

### Post by mgmiller on 2006-08-23
I just tried finding my digital camera using nautilus and I also can't figure out where it's getting mounted to.  But if you want to delete the pictures on it, just go to Applications > Graphics > GThumb Image Viewer.  It will mount the camera and allow you to delete the images.  You can select as many as you want and then right click and delete.  Or you can find the same commands in the file drop down menu.

---

### Post by ciscosurfer on 2006-08-23
Issue```
mount
```to see where your camera is mounted.  And then, go from there.

---

### Post by aleska on 2006-08-23
> **ciscosurfer said:**
> Issue```
mount
```to see where your camera is mounted.  And then, go from there.

You either missed my post above or wrote your reply simultaneously.  When I enter the command mount, before connecting my camera to the usb port, and after, there is no change.  That's to say, I don't believe mount picks up the camera.  I could be wrong.  

Here are the results to mount (again before and after connecting the camera)
> /dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
//linkstation1/share on /mnt/linkstation type smbfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)


I don't see which of those would be the camera...

---

### Post by aleska on 2006-08-23
BUMP
Any ideas other than "mount"?  "mount" doesn't seem to show it.

---

### Post by quonsar on 2006-08-24
if i decline the import prompt, nautilus automatically opens showing the camera files. give that a try.

if and when you DO find your camera, be sure to go into nautilus prefs and choose direct delete option to bypass trash bin. then your nautilus menu will have an additional option to immediately delete files rather than send them to the trash. 

if you dont do this, nautilus will create a trash folder in the root of your cameras memory card, which your camera wont recognize  and which it will not display in its file listing/preview. your deleted images will accumulate in there and fill up your cams memory.

---

### Post by gustolove on 2006-09-03
same issue here... i want to be able to mount my camera because i need to recover some pictures off of it...

i can import the current pictures on it but it is not showing when i type 'mount'

i see ne resolution above so i was wondering if anyone else had any ideas?

---

### Post by djprotoss on 2006-11-06
mount won't show anything as libgphoto doesn't mount the remote filesystem - it just queries the device.
There are a couple of ways you can get filesystem support on top - gnomevfs and gphotofs (based on fuse) - have a flick through the gphoto documentation.
Unfortunately my knowledge does not extend beyond that as the cli has proved adequate to my needs to date.

---

### Post by rmjb on 2006-11-06
Switch your camera to USB Mass Storage Mode instead of PictBridge or PTP. In this mode the camera will appear in Nautilus.

If your camera does not support this, a simple card reader will work.

- rmjb

---

