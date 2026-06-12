---
title: "Error Mounting IPOD."
date: 2005-12-19
forum: General Help
---

### Post by ctaborda on 2005-12-19
Whenever I plugin my ipod, I get an error that says 
"Unable to mount the selected volume"
Error: This program needs to be installed suid root
Error: Could not execute pmount

Well, the weirdness is that this was working perfectly before... Just now I got this error..

Please anyone help?

Carlos

---

### Post by BathroomNinja on 2005-12-19
Working before what?  When was the last time it worked.  Have you installed anything else since then?  Have you tried rebooting?

What is the actual command you are using to mount your iPod?

---

### Post by John Jason Jordan on 2005-12-19
[QUOTE=ctaborda]Whenever I plugin my ipod, I get an error that says 
"Unable to mount the selected volume"
Error: This program needs to be installed suid root
Error: Could not execute pmount

Well, the weirdness is that this was working perfectly before... Just now I got this error  ... Carlos[/QUOTE]
I've been going through the same problems. It used to automount just fine. But I haven't actually plugged it in for a couple months until recently. And in between I upgraded to Breezy (64-bit). So that may be the source of the problem. Of course, I am always trying out different other applications, so who knows where the problem came from.

Another place it may have come from is that I recently acquired a 60 Gb pocket hard disk that is also USB 2.0. MY iPod and the computer's internal hard disk are also 60 Gb, making it sometimes difficult to tell which is which. The pocket drive still automounts fine, but the iPod no longer automounts.

As a fix here is what I discovered (with the help of local Linux gurus):

1) do the command "dmesg | tail" I'm not sure what the purpose of this command is, but it seems to list everything that is on the USB ports, whether it is mounted or not. Look for "sda" or "sdb." For example, if the pocket drive is mounted first it will be sda, and if I then plug in the iPod it will be sdb. This will tell you what Linux thinks the drive is called. But note that the iPod has two partitions -- a small one that holds the database (I think) and the main one where everything else is installed. These will be "sda1" and "sda2" respectively (changing the "a" to "b" or whatever as necessary).

2) Once you know what Linux thinks the name of the iPod is, give the command: "sudo mount -t vfat -o umask=[your username goes here] /dev/sda2 /media/iPod." Here is what each component of that command means and why I found them all necessary:

sudo: Only root can mount a volume

-t vfat: My Ubuntu refused to mount it without being told it was formatted Fat32. I don't know why it couldn't see the format, but it kept complaining until I added this option. "-t" is the switch and "vfat" means Fat32.

-o umask=[your username]: I could mount the iPod without this option and I could read the files on it, but could not write to it. For some dumb reason Linux mounted it so that anyone could read it but only root could write to it. Since "sudo" means you are mounting it as root, you have the authority to give yourself (in your ordinary user status) permission to write to the iPod.

/dev/sda2: Change the "a" to whatever the dmesg | tail command tells you the iPod is. The "2" means you want to mount the second partition.

/media/iPod: This is the mount point. On my computer the mount pont is /media/iPod; that is, the folder already exists and that is where I want it to be mounted. You can use Nautilus to look at the /media folder to see what mount points you already have. It's probably "iPod" but it might be different. (Note that filenames and folders are case-sensitive, so "ipod" is not the same as "iPod.")

I still don't know why it no longer automounts. But at least the above gets it mounted for me.

IMPORTANT: For God's sake do not disconnect the iPod if it is mounted. Use the umount command to unmount it first. I found that the following is sufficient: "sudo umount /media/iPod." You may get away with unplugging it while it is still mounted, but it is also very likely that doing so will cause the iPod's filesystem to become corrupted. If that happens you will lose everything on the iPod. Not only that, you will have to find a Windows XP or Windows 2000 (Service Pack 4) computer with iTunes to reformat it and reinstall the directory structure and database. (There are people who claim to have used Linux tools to do this, but I found they do not work.)

Also, if you have a lot of stuff on your iPod, use a program like gtkpod to export your files frm the iPod to a backup medium. I do this every time after adding new mp3s to my iPod. I learned this the hard way (14 Gb of mp3s lost).

Hope that helps get you back running again.

---

