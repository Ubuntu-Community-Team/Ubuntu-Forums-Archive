---
title: "How to save file to floppy disk"
date: 2005-11-21
forum: Desktop Environments
---

### Post by sweeneysmsm on 2005-11-21
In my File Save As dialogue there does not seem to be a way to select a floppy disk drive as the file destination. I have tried to move up levels but I still remain in the laptop drive. Can you help? Help is greatly appreciated.

Mary

---

### Post by Ampersand on 2005-11-21
Have you mounted the floppy beforehand? I think Breezy has a few problems with floppies (although I don't have a floppy drive, so can't confirm this).

Anyway, after inserting a disk, type in a terminal:
```
sudo mount -t vfat /dev/fd0 /media/floppy
```
(Use ```
sudo mkdir /media/floppy
``` to create the directory if it doesn't exist)
You should then be able to save to /media/floppy.

---

### Post by sweeneysmsm on 2005-11-21
Thank you, Ampersaond.

Can you tell me how to get to this "terminal".  I'm a Windows girl...

Thanks,

Mary

---

### Post by not_yet on 2005-11-21
I'm away from my ubuntu machine, but have a look under applications or system for terminal

---

### Post by Ampersand on 2005-11-21
It's under the 'Applications - Accessories' menu. It's the equivelent of the Windows command prompt

---

### Post by kperkins on 2005-11-21
On your places tab  click on Computer.  If your floppy is mounted (it should automount if you insert a floppy disk) you should see it listed in that window along with your Cdrom drive and Filesystem. (actually, if it's mounted you should be able to see it in the left pane of the file save dialogue box--at least in gedit)  If you see it there, you can open it up and drag and drop whatever file you want to it.
If you don't see it, you'll have to mount it as mentioned above.
Terminal is located under applications > Accessories (or hit ALT+F2, and type gnome-terminal)

---

### Post by ed_d on 2005-11-21
OK, so the floppy is supposed to "automount"? Well mine dosent and when I try to mount it through the "Places>Computer" tab, says "Error: given UDI is not a mountable volume"
Now I can do 'mount /dev/fd0' or 'mount /media/floppy' and all is well. Any way to fix this so that I dont have to continue to mount via a terminal session? I even tried to use the "disk mounter" tab from add to panel, same result from above.
TIA

---

### Post by dubz on 2005-11-21
floppies will never automount as they are mechanical devices and have no way of telling when a disk is in the drive.

I find the best way to do it is from a terminal.thats how its been done for many years.It is surprising that your disk mounter doesnt work though.

try creating you own shortcut thingy on a toolbar. with the correct command thats you mentioned above where it says. command to run.
that should mount your drive from X.

hope this helped

thanks.

---

### Post by ed_d on 2005-11-21
I know that they do not auto mount, thus the question mark. Ill give it a try, think I had to do the same thing under core too.

---

### Post by dubz on 2005-11-21
My bad, i should really pay more attention to grammar. its my downfall.that solution should work as it worked on redhat6.2 through to FC2.

If it doesnt work ill be highly embarressed. oh well.
good luck.

---

### Post by ed_d on 2005-11-21
No worries. I did just make a "custom" app and it mounts the floppy fine. Just have to right click on the icon to unmount. All is good.

---

### Post by dubz on 2005-11-21
*sigh of relief*

---

### Post by kperkins on 2005-11-21
[QUOTE=dubz]floppies will never automount as they are mechanical devices and have no way of telling when a disk is in the drive.

I find the best way to do it is from a terminal.thats how its been done for many years.It is surprising that your disk mounter doesnt work though.

try creating you own shortcut thingy on a toolbar. with the correct command thats you mentioned above where it says. command to run.
that should mount your drive from X.

hope this helped

thanks.[/QUOTE]
Making your own shortcut is a solution, but I thought that Ubuntu was supposed to be newbie friendly. :D
[Rant]
Not having had a floppy drive for awhile, I forget how it actually works, but I know that a floppy drive can be mounted when you boot up your computer, it was being done on Mandrake (at least) several years ago (back when I still had a floppy drive).  And it's really bullshit to say that there's no way to tell if there's a disk in the drive, since Windows, and Apple have been able to tell for years when you insert a floppy in the drive, and, Linux can, too--try opening a floppy drive w/o a floppy in it.   It certainly can for a CDRom drive, or a USB port, so something as old as the floppy drive should be really well supported. (In fact looking into it deeper--thank you ask.com--the supermount patch can be included in most kernels, maybe it isn't in  Ubuntu? and autofs isn't installed by default either, we do, of course, have gnome-volume-manager, but I'm not sure if it's set up for automounting floppies, like it is everything else, or not.).
It should be as simple as having an entry in fstab to mount it at boot-up and then just insert a floppy, and select it like you would (say) your CDRom drive which shows up in the filesystem after bootup even with no media in it, and it can be.  
Probably the major reason it's not is that the floppy is a, virtual, thing of the past, so why support it?  Most new computers don't come with a floppy drive installed, unless you , specifically, ask for it.  Why bother when CD-RWs hold 800mb of data, and you can barely put anything on the measly 1.44mb floppy.
I don't know if that's the developers stand on this or not, and I'm not sure that it's not a bug, but it is a pain for those people who still use floppies.  If they can auto mount a CD, why not the older, more basic floppy?
[/Rant]

---

### Post by dubz on 2005-11-21
find a windows or mac box,let it boot then shove in a floppy...does anything popup telliong you there is a disk in the drive?i think not.thats what i was trying to get across.

---

### Post by kperkins on 2005-11-21
PS Inserting a floppy in my floppy drive on my Debian print/file server lets me see the files on the floppy (from the command line) without having to manually mount it.  Why can't Ubuntu do the same?

---

### Post by kperkins on 2005-11-21
[QUOTE=dubz]find a windows or mac box,let it boot then shove in a floppy...does anything popup telliong you there is a disk in the drive?i think not.thats what i was trying to get across.[/QUOTE]
OK now I see your point.  :D

---

### Post by ed_d on 2005-11-21
If I didnt need to use the floppies to load microcode, I wouldnt bother. But this is the fun of linux, making your system work the way you want.......

---

### Post by ed_d on 2005-11-22
Interesting update.....
Apears that in the last update, I can now go to Places>Computer and mount a floppy by right clicking on the device. Wonder if someone was reading the forum and added the update.......

---

### Post by patrihito on 2005-12-08
[QUOTE=Ampersand]
Anyway, after inserting a disk, type in a terminal:
```
sudo mount -t vfat /dev/fd0 /media/floppy
```
(Use ```
sudo mkdir /media/floppy
``` to create the directory if it doesn't exist)
You should then be able to save to /media/floppy.[/QUOTE]

I did like mentioned by Ampersand but I can save files only as root and only using the terminal - is there no other solution?

This is how I manage to save files to my floppy:

```
sudo cp myfile /home/myname/floppy/
```

It would be really nice to be able to use the mounted floppy just like any other drive.

Thanx.

patrihito

---

### Post by canadianwriterman on 2005-12-08
[QUOTE=ed_d]Interesting update.....
Apears that in the last update, I can now go to Places>Computer and mount a floppy by right clicking on the device. Wonder if someone was reading the forum and added the update.......[/QUOTE]

This is how floppy mounting is supposed to work in Breezy. It saves all the terminal entries and creating an icon on your desktop, etc. I prefer to have the functionality working as it was really designed to. 

Unfortunately, there were many people (myself included) for whom this function did not work. There was a bug in the **pmount** file that controls mounting. Developers fixed the file, but it was not sent out as an update. But, you can update it yourself.

To update pmount, go to:

**[http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/](http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/)**

Download and install **pmount_0.9.6-1_i386.deb**

---

### Post by sweeneysmsm on 2005-12-28
Sorry to be so long in replying but I have been away.

Thank you so much for the reply. I am new to Linux and trying to help someone who is also very new.

The Linux laptop we are using does not have an internet connection. I therefore downloaded the file you suggested - hope it's the right one as it included a mention of breezy in the path. I dowloaded it to a floppy disk on a Windows machine.

Can you tell me exactly what I have to do to "install" the file. If it was Windows I would just go to My Computer/A and double click on an executable file, but my problem is in getting these things mounted as it doesn't seem to find the Floppy intuitively. Is this .deb file executable?

Thank you again for your help.

Mary

---

### Post by Sef on 2006-01-04
Canadianwriterman: Thank you.  My floppy drive automounts now.

Mary:

> an you tell me exactly what I have to do to "install" the file. If it was Windows I would just go to My Computer/A and double click on an executable file, but my problem is in getting these things mounted as it doesn't seem to find the Floppy intuitively. Is this .deb file executable?

Do this to get it to automount:

There is a bug in Breezy, so often the floppies won't automount. To get them to automount, go to this site:

[http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/](http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/)

1) Download pmount_0.9.6-1~breezy1_i386.deb

2) Install --> sudo dpkg -i pmount_0.9.6-1~breezy1_i386.deb

3) enter password

4) After it finishes installing, your floppy should mount and umount automatically.

It is from this thread:  [http://ubuntuforums.org/showthread.php?t=110132&page=2]("http://ubuntuforums.org/showthread.php?t=110132&page=2")

---

### Post by tastyturkey on 2006-02-09
I cannot write to floppies in Ubuntu Breezy.

I can mount them but I cannot write to them.

I should add that I can write to a floppy if I mount it from the command line but I need it to write to the floppy using GUI programs. My family has Ubuntu on their computers now and they do not do the command line.

---

### Post by Guns90 on 2006-04-26
sef, 

I just did the download and install of the patch and this is the respose...
dpkg: error processing pmount_0.9.6-1~breezy1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 pmount_0.9.6-1~breezy1_i386.deb
gary@GARY:~$

Any suggestions?

---

### Post by Guns90 on 2006-04-26
Never mind.   Here is a post I received from someone on another forum and I can now copy to my floppy with no problems.  I've tested it in another Windows machine and it seems to working perfectly.  

Ok, I have the book "Beginning Ubuntu Linux From Novice to Professional" and was able to use it to figure out how to copy files to floppy without using the command line.

1.)Format the floppy(use FAT if sharing with Windows) by Applications--System Tools--Floppy Formater

2.)Click on Places--Computer, then double-click floppy icon, this will mount the floppy drive and place an icon on the desktop. Then just drag and drop the file you want copied onto the desktop icon. I just did it with the OpenOffice file that I created earlier and it worked.

3.) When you're finished, right click on the desktop floppy icon, unmount(icon will disappear), eject floppy.

I believe this book will be pretty useful in using Ubuntu...

Oh, and someone said they couldn't understand  why someone would use a floppy these days, I agree; however, the schools still us them and unfortunately do not have CD-RW's.

---

### Post by Stuperfied on 2006-04-30
I did this, it works. You have to insert disk, mount, perform action, unmount, remove disk and then begin again which is prety tiresome. Its a shame that it cant work like windows. I will probably try to get a script that will mount and unmount everytime for me.

---

