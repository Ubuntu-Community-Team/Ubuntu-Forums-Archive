---
title: "Auto mounting hell!"
date: 2005-12-08
forum: Desktop Environments
---

### Post by rozojc on 2005-12-08
Well, I changed from Ubuntu to Kubuntu and it seemed to solve an issue I had with Gnome (plus it looks better :-) )

Anyway, l've not been a KDE user and I'm having a lot of trouble right now with my external hard drive.
It was working fine, and then I decided to re partition it. I changed several things and now I (supposedly) have a 90Gigas or so ext3 partition and 30 G free that will be NTFS (I need to handle over 4 giga files in Windows so I need it...).

Anyway, by some reason Linux seems not to understand that I changed and formated the partitions!!! Each time I plug the hard drive Linux is trying to automount it like it was before I reformatted partitions and all. Obviously, I just plug it in and KDE tries to open Konqeror, a crash (failure) sounds through my speakers And I get a message saying "Could not mount device", another saying "The file or folder media:/sda2 does not exist.", and I just can't mount them. If I insist, eventually "I get it mounted, but I can't write into it because it gets mounted as read only!!! Oh, and I also get this small windows showing the process of automount which get stuck at 0% and I have to press "Cancel"...

Any ideas? I've been struggling with this for the last hour and I am getting a little bit tired of this not working...

---

### Post by rozojc on 2005-12-08
Oh, and I just noticed that when it does mount, it reports the 90G partition as being NTFS (which is not)

---

### Post by mlomker on 2005-12-08
Do you have entries in /etc/fstab for that drive?  Is the behavior the same if you reboot with the drive plugged in?

I've had problems with plugging/unplugging flash drives and eventually confusing the operating system.

---

### Post by rozojc on 2005-12-08
Nope, fstab does not have entries for that drive (it's never had and before I repartitioned it worked). After hours of tweaking I was able to reformat (again) the hard drive as ext3, and it seems it is now recognizing it as it should... I just hope I don't have any more trouble from this drive...

---

### Post by mlomker on 2005-12-09
[QUOTE=rozojc]Nope, fstab does not have entries for that drive (it's never had and before I repartitioned it worked).[/QUOTE]

Yeah, the **pmount** program will automount pluggable devices without an fstab entry.  I asked because an entry would over-ride pmount's behavior.  If it's a drive that you normally have connected then I'd recommend an entry...if for no other reason than creating a fixed mount point.

---

### Post by rozojc on 2005-12-09
New problem!!!

I hadn't tried loading CDs, but now everytime I do Kubuntu tries to automount, and it fails. It opens konqueror with a message saying:

An error occurred while loading media:/hdc:
The file or folder media:/hdc does not exist.


How can I fix this? I mean, this should work fine, shouldn't it?

ps/ I don't have an entry for it on fstab

---

### Post by cwaldbieser on 2005-12-09
[QUOTE=rozojc]New problem!!!

I hadn't tried loading CDs, but now everytime I do Kubuntu tries to automount, and it fails. It opens konqueror with a message saying:

An error occurred while loading media:/hdc:
The file or folder media:/hdc does not exist.


How can I fix this? I mean, this should work fine, shouldn't it?

ps/ I don't have an entry for it on fstab[/QUOTE]

It sounds like it is just looking for the folder /media/hdc to mount the cdrom.  Look in /media and see if you have an hdc folder.  If you have something like a cdrom folder, just create a symlink and call it hdc, and maybe that will take care of the problem.

---

### Post by rozojc on 2005-12-09
[QUOTE=cwaldbieser]It sounds like it is just looking for the folder /media/hdc to mount the cdrom.  Look in /media and see if you have an hdc folder.  If you have something like a cdrom folder, just create a symlink and call it hdc, and maybe that will take care of the problem.[/QUOTE]

Nope, didn't work, I actually created a folder named hdc and didn't work. I then went one level higher from where KDE writes the error and according to the location bar it's somewhere called  "media:/". I thought "I'll just create a folder in this place" but I have no writing permissions, no way to become root in there (that I know of) and I don't even know where that folder is physically in order to create the folder manually via sudo...


Any ideas? Anyone know where this folder  "media:/" is?

---

### Post by Sokraates on 2005-12-09
Try the following command in a terminal:

```
sudo ln -s /dev/hdc /media/hdc
```

"sudo" is the command to start an app (here: ln) as root. You will be prompted for our user-password afterusing sudo.

The command above will create a link ("ln") from the first IDE-device on the second IDE-cable (usually your CD-ROM) to the directory "media".

**Edit:** "media:/" usually lists all devices found in "/media"

---

### Post by rozojc on 2005-12-09
[QUOTE=Sokraates]Try the following command in a terminal:

```
sudo ln -s /dev/hdc /media/hdc
```

"sudo" is the command to start an app (here: ln) as root. You will be prompted for our user-password afterusing sudo.

The command above will create a link ("ln") from the first IDE-device on the second IDE-cable (usually your CD-ROM) to the directory "media".

**Edit:** "media:/" usually lists all devices found in "/media"[/QUOTE]
Didn't work... Also media:/  appears completely empty...

I've been searching on google for some quite now... I found something saying it's a problem related to a daemon called ivman which actually doesn't use fstab but hal and some other stuff in order to work... I'm getting kind of desperate now... I switched from Ubuntu to Kubuntu because of a problem with Xorg and haven't had it since (so I guess it was Gnome related), but now I'm having this issue and I really wouldn't like to leave the distro cause I like it a lot...

HELP!!!

I don't even know if media:/ is even like a "real" folder or how does this ivman thing works (I mean, I'm able to do a couple of things in linux but I'm not a guru or anything...)

Any more ideas?

---

### Post by cwaldbieser on 2005-12-09
[QUOTE=rozojc]Didn't work... Also media:/  appears completely empty...

I've been searching on google for some quite now... I found something saying it's a problem related to a daemon called ivman which actually doesn't use fstab but hal and some other stuff in order to work... I'm getting kind of desperate now... I switched from Ubuntu to Kubuntu because of a problem with Xorg and haven't had it since (so I guess it was Gnome related), but now I'm having this issue and I really wouldn't like to leave the distro cause I like it a lot...

HELP!!!

I don't even know if media:/ is even like a "real" folder or how does this ivman thing works (I mean, I'm able to do a couple of things in linux but I'm not a guru or anything...)

Any more ideas?[/QUOTE]

ivam is "Ike's Volume Manager".  It is what is being used in Kubuntu Breezy for automounting.  In KDE 3.5, I believe they have auto-mounting built in.

There are some config files for ivman in /etc/ivman.  Mabe one of them has solution to your problem in it?

---

### Post by rozojc on 2005-12-09
I just checked those. They're a couple of well documented XMLs, but nothing that could solve my problem. Apparently it's actually configured to try to automatically mount anything that's mountable, but on the XML you just set that parameter (meaning: I don't know how it's trying to mount it and therefore I don't know why it's failing to mount). What I do know now is that the problem is not with konqueror opening media:/ but apparently the problem is that ivam is not succesfully mounting it (it does receive the message from hal that something was plugged in but fails to mount it)...

Regarding KDE 3.5. You say in 3.5 automounting is built-in. Is there anyway to install 3.5 via apt-get, or would I have to like download it and build it (which I'm not really up to it...)

---

### Post by Sokraates on 2005-12-10
For KDE 3.5 on Kubuntu take a look at the [official announcement](http://kubuntu.org/announcements/kde-35.php) on kubuntu.org.

Download the key, add the repository to synaptic and have fun installing. :D 

If you want to know more about the new features, take a look at the [visual guide to KDE 3.5](http://www.kde.org/announcements/visualguide-3.5.php).

Tell us, if KDE 3.5 fixes your problem.

---

### Post by rozojc on 2005-12-10
[QUOTE=Sokraates]For KDE 3.5 on Kubuntu take a look at the [official announcement](http://kubuntu.org/announcements/kde-35.php) on kubuntu.org.

Download the key, add the repository to synaptic and have fun installing. :D 

If you want to know more about the new features, take a look at the [visual guide to KDE 3.5](http://www.kde.org/announcements/visualguide-3.5.php).

Tell us, if KDE 3.5 fixes your problem.[/QUOTE]
Well, I now have a nicer desktop with all of KDEs 3.5 features. Removable drives get mounted nicely as well as audio CDs (there's even a window asking the typical "What would you like to do?" stuff. But it doesn't seem to be working well with either data CDs or DVDs. With DVDs I continue to have the same problem, and with data CDs they get mounted alright. Actually they get so well mounted it is then impossible to unmount them as the device always claims to be busy...

I'm getting desperate...

---

### Post by Sokraates on 2005-12-10
[QUOTE=rozojc]Well, I now have a nicer desktop with all of KDEs 3.5 features. Removable drives get mounted nicely as well as audio CDs (there's even a window asking the typical "What would you like to do?" stuff. But it doesn't seem to be working well with either data CDs or DVDs. With DVDs I continue to have the same problem, and with data CDs they get mounted alright. Actually they get so well mounted it is then impossible to unmount them as the device always claims to be busy...

I'm getting desperate...[/QUOTE]

The windows-esque "What do you want to do" is introduced by KDE 3.5.

As far as I can tell, your problem does not lie with KDE. I had the same problem once, with CDs always considered busy. I deleted something back then, but don't remember, what it was.

Looking into synaptic, I see autofs, fdutils and pmount installed. ivmount, gnome-volume-manager and usbmount are deleted.

Try uninstalling anything but those three. Maybe it helps. As for DVDs: do you have libdvdcss2 installed?

---

### Post by cwaldbieser on 2005-12-10
[QUOTE=rozojc]I just checked those. They're a couple of well documented XMLs, but nothing that could solve my problem. Apparently it's actually configured to try to automatically mount anything that's mountable, but on the XML you just set that parameter (meaning: I don't know how it's trying to mount it and therefore I don't know why it's failing to mount). What I do know now is that the problem is not with konqueror opening media:/ but apparently the problem is that ivam is not succesfully mounting it (it does receive the message from hal that something was plugged in but fails to mount it)...

Regarding KDE 3.5. You say in 3.5 automounting is built-in. Is there anyway to install 3.5 via apt-get, or would I have to like download it and build it (which I'm not really up to it...)[/QUOTE]

Here is the visual guide where the removable media stuff is mentioned: 
[http://www.kde.org/announcements/visualguide-3.5.php]("http://www.kde.org/announcements/visualguide-3.5.php")

And here is the link to the Kubuntu package:
[http://kubuntu.org/announcements/kde-35.php]("http://kubuntu.org/announcements/kde-35.php")

I would suggest asking around how others have fared using it first before jumping right in.  I tend to be a little more on the conservative side and wait for the desktops to be released with the distro, so I will probably be using KDE 3.4 until Dapper Drake.

Don't know if you tried this, but can you mount your CDROM from the terminal with "pmount"?

---

### Post by cwaldbieser on 2005-12-10
[QUOTE=rozojc]Well, I now have a nicer desktop with all of KDEs 3.5 features. Removable drives get mounted nicely as well as audio CDs (there's even a window asking the typical "What would you like to do?" stuff. But it doesn't seem to be working well with either data CDs or DVDs. With DVDs I continue to have the same problem, and with data CDs they get mounted alright. Actually they get so well mounted it is then impossible to unmount them as the device always claims to be busy...

I'm getting desperate...[/QUOTE]
When I get that error, it is usually because some process (usually konqueror) is out there holding on to it.

```

$ lsof /dev/hdc

```
should identify the culprit.  Then you can kill the process and unmount the drive.  It may also give you a clue as to what the problem is.

I have only ever experienced this problem with some comercial CDs .  For example, I had "Dungeon Siege II" sitting in the CD tray, but forgot what was in there.  I was to lazy to pop the drive open, so I thought I'd just browse the directory-- and it mounts but I can hear the drive still making noises.  Konqueror kinda froze at that point, so I closed it, but I couldn't unmount the drive.  The command I gave you showed me that the konqueror process was still hanging out there.  Once I killed it, the drive unmounted normally.

---

