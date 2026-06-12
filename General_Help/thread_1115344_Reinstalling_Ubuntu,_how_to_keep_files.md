---
title: "Reinstalling Ubuntu, how to keep files"
date: 2009-04-03
forum: General Help
---

### Post by BananaUnicorn on 2009-04-03
First off yes im a total Linux noob so this question may seem dumb



But I want to reinstall and am unsure of how to keep any files, im  assuming any installed apps will be gone? but what about files in my home directory?


Should I move them to some backup folder on the filesystem?


Or does everything get wiped.


basically......how do I NOT mess up the simple task of reinstallation :lolflag:

---

### Post by ShaunG on 2009-04-03
When you do a reinstall only the partition you choose to install onto will be wiped.

I suggest copying the contents of your home folder to an external hard drive/usb/partition that you won't be installing onto. Then re-install and copy the contents of your old home folder back.

Make sure you copy all of the contents though and not just the unhidden files. From a command line you could type

```
cd
sudo cp -r * /mnt/<name of partition/usb/whatever>
```

This will copy all of the contents of your home directory to /mnt/whatever

EDIT:

See [http://ubuntuforums.org/showthread.php?p=1990911](http://ubuntuforums.org/showthread.php?p=1990911) for a quick guide on creating a list of installed apps and re-installing those applications.

Or [http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/]("http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/")


Hope this helps.

---

### Post by BananaUnicorn on 2009-04-03
I tried to connect an external HDD and it refused to mount saying


The Logfile indictates an unclean shutdown (0,0) Failed to mount '/dev/sdb1': Operation not supported Mount is denied becase NTFS is marked to be in use


there was more but the command line option it gave me didnt do anything

---

### Post by ShaunG on 2009-04-03
Have you ntfs-3g installed?

Try this (taken from [http://ubuntuforums.org/showthread.php?t=659312](http://ubuntuforums.org/showthread.php?t=659312) )

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1

```

If you still get an error message you can either stick it in a windows pc, and unmount it properly via the safely remove hardware or you can force it to mount with

```
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
```

This might help.

---

### Post by BananaUnicorn on 2009-04-03
> **ShaunG said:**
> Have you ntfs-3g installed?

Try this (taken from [http://ubuntuforums.org/showthread.php?t=659312](http://ubuntuforums.org/showthread.php?t=659312) )

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1

```

If you still get an error message you can either stick it in a windows pc, and unmount it properly via the safely remove hardware or you can force it to mount with

```
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
```

This might help.

Got ntfs-3g installed, didnt have it at first

followed next steps, still didnt work
"
Error reading bootsector: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation"



Failure in every step I take =(

Edit: It worked after a reboot and copying backup onto it now!


Thanks alot for your help :D

and thanks for showing me a way keep a list of all installed programs

---

### Post by ShaunG on 2009-04-03
Every thing that you try and fail is another lesson learned. 

Do you have a windows pc? If so, stick the hard drive into that, it should mount, then safely remove it. 

Restart your ubuntu box and then plug the usb into that. It should automount, should.

Sorry, I've only been using ubuntu for a little over a year and I am new to some things to. However I did have this same problem and managed to fix it by force mounting it . Apologies that so far I've not been much help.

---

### Post by tjwoosta on 2009-04-03
this is exactly the reason why its always good to have a seperate /home partition

---

### Post by ShaunG on 2009-04-03
tjwoosta makes a good point. Having a seperate home partition is a very good idea but you're more than welcome, I'm glad I could be of service.

---

### Post by BananaUnicorn on 2009-04-03
When I reinstall I'll make a seperate partition, and it was useful to work out how to get an external drive working anyway :D

---

### Post by ShaunG on 2009-04-03
Generally for external hardrives/usbs they will automount fine.

If they are formatted as ntfs you will need ntfs-3g to mount them but with that installed any ntfs ext hard drive should auto-mount fine.

And if there is a problem mounting, for example they won't mount because of an unclean unmount (yanking it out of a windows box) you can force it to mount from the command line. Or you can re-mount on the windows box and unmount safely.

Also you could probably tick this thread as solved?

---

### Post by firefly2442 on 2009-04-04
> **tjwoosta said:**
> this is exactly the reason why its always good to have a seperate /home partition

This is a good idea because most of your configurations and settings are stored in your home directory (. hidden files usually) so the next time you install you may only have to do a little tweaking before everything is back to normal.

---

