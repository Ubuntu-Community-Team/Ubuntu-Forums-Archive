---
title: "Newbie: Need help mounting Windows hard drive (hda, ntfs) AND kubuntu desktop."
date: 2006-02-19
forum: Desktop Environments
---

### Post by nmastae on 2006-02-19
I am a newbie to Linux, though I'm relatively experienced with the nuts-and-bolts of Windows. I can't figure out how to mount my Windows hard drive, hda, ntfs file system. (Ubuntu is on hdb.)

I tried: 

jane@...2:~$ sudo mkdir /media/Windows
PW
jane@...:~$ sudo mkdir /media/Windows
mkdir: cannot create directory `/media/Windows': File exists
jane@...:~$ sudo mount -t ntfs /dev/hdb5 /media/windows mount: mount point /media/windows does not exist
jane@...:~$ sudo mkdir /media/Windows
mkdir: cannot create directory `/media/Windows': File exists
jane@...:~$ sudo mount -t ntfs /dev/hdb5 /media/windows
mount: mount point /media/windows does not exist


but, obviously, this didn't work.

All guidance gratefully received!


Also, please walk me through how to install the kubuntu desktop. I see KDE-desktop in the Synaptic utility, but don't know which of these many options to choose: I'd rather just start with the "packaged deal"!

Thanks a million!

Jane

---

### Post by aysiu on 2006-02-19
Can you post the output of these three commands? ```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by nmastae on 2006-02-19
[QUOTE=aysiu]Can you post the output of these three commands? ```
sudo fdisk -l
cat /etc/fstab
df -h
```[/QUOTE]

Hey, thanks for getting back to me so quickly! :)

Here's what I got:

Disk /dev/hda: 13.6 GB, 13600677888 bytes
255 heads, 63 sectors/track, 1653 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1652    13269658+   7  HPFS/NTFS

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2330    18715693+  83  Linux
/dev/hdb2            2331        2434      835380    5  Extended
/dev/hdb5            2331        2434      835348+  82  Linux swap / Solaris
jane@...:~$

---

### Post by aysiu on 2006-02-19
What about the other commands (*cat /etc/fstab* and *df -h*)?

Well, we'll see what we can do. Try this: ```
sudo umount /dev/hda1
sudo mkdir /windows
sudo cp /etc/fstab /etc/fstab_backup
sudo kwrite /etc/fstab
``` Once KWrite opens look for the line with /dev/hda1 in it. It'll probably be something like this: ```
/dev/hda1 /media/windows ntfs defaults 0 0
``` **_Replace_ that line with this one**: ```
/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
``` Make sure there is _only one line_ that makes reference to /dev/hda1. Then save and close the document. Finally ```
sudo mount -a
```

---

### Post by nmastae on 2006-02-19
Should I install the kubuntu-desktop before I try this? Eventually that's the interface I want to use. If so, can you tell me how to do that?

Thanks so much for your help.

---

### Post by aysiu on 2006-02-19
[QUOTE=nmastae]Should I install the kubuntu-desktop before I try this? Eventually that's the interface I want to use. If so, can you tell me how to do that?

Thanks so much for your help.[/QUOTE] I'm sorry. I didn't realize you hadn't installed Kubuntu yet.

You can do this *before* you install Kubuntu if you want--just change the ```
sudo kwrite /etc/fstab
``` to ```
sudo gedit /etc/fstab
``` if you're in Gnome or ```
sudo nano /etc/fstab
``` if you're working off of a server installation.

To install Kubuntu, just type ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

---

### Post by nmastae on 2006-02-20
jane@69-12-151-212:~$ sudo get-apt install kubuntu-desktop
sudo: get-apt: command not found
jane@69-12-151-212:~$ sudo get apt install kubuntu-desktop
sudo: get: command not found
jane@69-12-151-212:~$ $sudo apt-get install kubuntu-desktop
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
jane@69-12-151-212:~$


Okay, so I tried to install Kubuntu with the Synaptic utility. It was up to 123 files when my PDA, which was connected to the USB port, got involved and stopped it in it's tracks. :( I tried to reinstall those files but nothing happens. I tried rebooting to see if maybe KDE was already installed, but it wasn't (no option to boot into Kubuntu. User error... grrr... 

So then I tried to do this in the terminal, but as you can see from the above, that didn't work either.

Now, I ran the following script before installing KDE, but it didn't seem to take, either. I feel like I'm back at Square One with Windows!

$ sudo -s -H
#cd /usr/share/applications
#for i in *.desktop; do \
# if ! grep -q ^OnlyShowIn= $i; then \
# echo ‘OnlyShowIn=GNOME;’ >> $i \
# fi
#done

The idea is that you follow it (in KDE, I suppose) with this script:
$cd /usr/share/applications/kde
$sudo -s -H
#for i in *.desktop; do
# if ! grep -q ^OnlyShowIn= $i; then
# echo ‘OnlyShowIn=KDE;’ >> $i
# fi
#done

The good news is that there is a media/windows file established.  I will now try your above suggestions. Meanwhile, can you tell me how to untangle my KDE mess?

Thanks!

Jane

---

### Post by aysiu on 2006-02-20
[QUOTE=nmastae]```
jane@69-12-151-212:~$ $sudo apt-get install kubuntu-desktop
[b]E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory[/b]
jane@69-12-151-212:~$
```[/quote] This is usually the kind of error you get when you're trying to apt-get and already have Synaptic or Adept open at the same time.

Try closing Adept and Synaptic and then running this command: ```
sudo killall apt-get
``` and then doing a ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

> 
Now, I ran the following script before installing KDE, but it didn't seem to take, either. I feel like I'm back at Square One with Windows!
```

$ sudo -s -H
#cd /usr/share/applications
#for i in *.desktop; do \
# if ! grep -q ^OnlyShowIn= $i; then \
# echo &#8216;OnlyShowIn=GNOME;&#8217; >> $i \
# fi
#done
```

The idea is that you follow it (in KDE, I suppose) with this script:
```
$cd /usr/share/applications/kde
$sudo -s -H
#for i in *.desktop; do
# if ! grep -q ^OnlyShowIn= $i; then
# echo &#8216;OnlyShowIn=KDE;&#8217; >> $i
# fi
#done
```  I don't know what this means. What are these scripts supposed to do? Where did you get them from?

---

### Post by jamesr on 2006-02-20
Hi nmastae

> jane@...:~$ sudo mount -t ntfs /dev/hdb5 /media/windows mount: mount point /media/windows does not exist
jane@...:~$ sudo mkdir /media/Windows
mkdir: cannot create directory `/media/Windows': File exists
jane@...:~$ sudo mount -t ntfs /dev/hdb5 /media/windows
mount: mount point /media/windows does not exist


 in the original problem you are creating the mount point 
 /media/Windows
and then trying to mount 
/media/windows

I am not sure if the mount points are case sensitive or not but it may be worth trying sudo mount /media/Windows

Also when you listed the sudo fdisk -l output part of which I am quoting

> Device Boot Start End Blocks Id System
/dev/hdb1 * 1 2330 18715693+ 83 Linux
/dev/hdb2 2331 2434 835380 5 Extended
/dev/hdb5 2331 2434 835348+ 82 Linux swap / Solaris

it shows hdb5 as a swap but you are trying to mount it as the ntfs partition ?

It would good to list > Can you post the output of these three commands? 
Code:
sudo fdisk -l
cat /etc/fstab
df -h__________________


as aysiu was requesting

---

### Post by aysiu on 2006-02-20
[QUOTE=jamesr]
 in the original problem you are creating the mount point 
 /media/Windows
and then trying to mount 
/media/windows

I am not sure if the mount points are case sensitive or not but it may be worth trying sudo mount /media/Windows[/QUOTE] Wow! I didn't even notice that. Good eye! Yes, it is case-sensitive.

---

### Post by nmastae on 2006-02-20
I was so concerned that I'd really messed things up that I simply reformatted the hard drive and reinstalled Ubuntu.  So,  I'm going to take it from the top with a clean slate.

Regarding problem #1: Mounting the Windows hard drive (hda):
Here's the  answer to the missing information (sorry to have let this slip by before...):

sudo fdisk -l
cat /etc/fstab
df -h

sudo fdisk -l
df: invalid option -- s
Try `df --help' for more information.
jane@...:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
jane@...:~$ df -hsudo fdisk -l
df: invalid option -- s
Try `df --help' for more information.
jane@...:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
jane@...:~$ df -h

(I have no idea what all this means!)

So, I will await your kind instructions for how best to mount this drive.
Then I will do the apt-get for kubuntu-desktop.

The script above came from: 
[http://ubuntu.wordpress.com/2006/01/13/ubuntu-to-kubuntu-keeping-the-menus-clean/](http://ubuntu.wordpress.com/2006/01/13/ubuntu-to-kubuntu-keeping-the-menus-clean/)

It is supposted to keep the menus clean.
What do you think? Worth trying? 

Someone else suggested using Kmenu-gnome to do something similar: apparently this application puts all the Gnome apps in a sub-menu in KDE.

Is there something similar that will contain the KDE apps in the Gnome menu?

I sure do appreciate you-alls help!

Jane

---

### Post by aysiu on 2006-02-20
[QUOTE=nmastae]```

sudo fdisk -l
df: invalid option -- s
Try `df --help' for more information.
```[/quote] I probably should have been more specific. Those three commands should all be entered separately. In any case, I'll go with what we have, and I'll assume the *sudo fdisk -l* you did earlier is still valid (meaning that your NTFS partition is at /dev/hda1).

> ```

jane@...:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```
(I have no idea what all this means!) Okay. I'll break it down for you:

**sudo fdisk -l** lists all your partitions and what filesystem types they are (regardless of whether they are mounted or not).

**df -h** lists what is *currently* mounted and where.

**cat /etc/fstab** lists _what_ should be mounted at boot-up time, _where_ those partitions and devices should be mounted and _how_ they should be mounted.
> So, I will await your kind instructions for how best to mount this drive.
Then I will do the apt-get for kubuntu-desktop. Actually, you can do the *sudo apt-get install kubuntu-desktop* at any time--it's totally independent of mounting the drive. Okay. What I'm going to suggest is that you copy and paste these commands instead of retyping them. The number one newbie mistake is mistyping (believe me--I've had my share of typos), and, as jamesr pointed out, all commands and files are case sensitive. Also, make sure you copy one line at a time. The "paste" shortcut in the terminal is **Shift-Insert**.

1. Open a terminal. Copy and paste this command: ```
sudo umount /dev/hda1
``` This unmounts your Windows partition in the off chance it happens to be mounted.

2. ```
sudo mkdir /windows
``` This command creates a directory (or **m**a**k**es a **dir**ectory) called *windows*.

3. ```
sudo cp /etc/fstab /etc/fstab_backup
``` This command makes a backup copy of your old /etc/fstab file in case we screw it up somehow.

4. ```
sudo nano /etc/fstab
``` This command lets us edit the /etc/fstab file. I'm using Nano as an editor because it's desktop agnostic (it can be used in both Ubuntu (Gnome) or Kubuntu (KDE)).

5. Once you're in your /etc/fstab file, create a new line by copying and pasting this into a blank space: ```
/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
```

So, ultimately, your /etc/fstab will look like this: ```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hdb1 / ext3 defaults,errors=remount-ro 0 1
/dev/hdb5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
```

6. Save the file by pressing Control-X (save), then y (confirm), and then Enter (exit).

7. Finally copy and paste in ```
sudo mount -a
``` this remounts whatever's specified as to be mounted in the /etc/fstab without having to reboot the entire computer.

> 
The script above came from: 
[http://ubuntu.wordpress.com/2006/01/13/ubuntu-to-kubuntu-keeping-the-menus-clean/](http://ubuntu.wordpress.com/2006/01/13/ubuntu-to-kubuntu-keeping-the-menus-clean/)

It is supposted to keep the menus clean.
What do you think? Worth trying? No. I think you should just get more comfortable with Ubuntu in general. You can always manually delete entries using the menu editor.

---

### Post by jamesr on 2006-02-20
Following on from aysiu suggestions I will modify to not use any of the KDE calls Sorry aysiu

Sorry changed my mind. Big edit.

Since you have completed a rebuild, it would be good to start at the beginning

Can you post the output of these three commands again? but from the new system.

```

sudo fdisk -l
cat /etc/fstab
df -h

```

---

### Post by nmastae on 2006-02-20
Nuts! I just did all that aysiu suggested. I will do those console commands now and report back. Can I undo the above moves?

---

### Post by nmastae on 2006-02-20
[QUOTE=jamesr]Following on from aysiu suggestions I will modify to not use any of the KDE calls Sorry aysiu

Sorry changed my mind. Big edit.

Since you have completed a rebuild, it would be good to start at the beginning

Can you post the output of these three commands again? but from the new system.

```

sudo fdisk -l
cat /etc/fstab
df -h

```[/QUOTE]



sudo fdisk -l

Disk /dev/hda: 13.6 GB, 13600677888 bytes
255 heads, 63 sectors/track, 1653 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1652    13269658+   7  HPFS/NTFS

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2330    18715693+  83  Linux
/dev/hdb2            2331        2434      835380    5  Extended
/dev/hdb5            2331        2434      835348+  82  Linux swap / Solaris



cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0



df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              18G  2.0G   15G  12% /
tmpfs                 380M     0  380M   0% /dev/shm
tmpfs                 380M   13M  367M   4% /lib/modules/2.6.12-9-386/volatile
/dev/hda1              13G  7.6G  5.1G  60% /windows


Please respond ASAP as I'm very worried about what I just did!

---

### Post by aysiu on 2006-02-20
It looks as if you followed the directions correctly!

So... you should be able to see your Windows partition in the /windows folder. Go ahead and open up Nautilus (in Gnome) or Konqueror (in KDE) and navigate to the /windows folder.

Do you see anything?

---

### Post by nmastae on 2006-02-20
[QUOTE=aysiu]It looks as if you followed the directions correctly!

So... you should be able to see your Windows partition in the /windows folder. Go ahead and open up Nautilus (in Gnome) or Konqueror (in KDE) and navigate to the /windows folder.

Do you see anything?[/QUOTE]

I am not in Ubuntu at the moment as I had to boot up Windows to get my email. (Just installed Ubuntu yesterday, and am not yet ready to migrate the essentials...)

What was Jim R., above, saying? Should be have gone about this mounting process differently? Is there anything here I need to undo?

I will boot into Ubuntu soon and post a report.  I didn't see the disk mounted in the Computer menu, or in media, but I didn't look in Nautilus.

Oye veh!

---

### Post by aysiu on 2006-02-20
[QUOTE=nmastae]I am not in Ubuntu at the moment as I had to boot up Windows to get my email. (Just installed Ubuntu yesterday, and am not yet ready to migrate the essentials...)

What was Jim R., above, saying? Should be have gone about this mounting process differently? Is there anything here I need to undo?[/quote] No. As I said before, you appear to have done everything correctly. The instructions I gave you were based on guesses, since I didn't get all three commands. James just wanted to be sure we were doing things right, so he asked for all three commands again.

> 
I will boot into Ubuntu soon and post a report.  I didn't see the disk mounted in the Computer menu, or in media, but I didn't look in Nautilus.

Oye veh! It may not appear as a "mounted disk," but it should appear in the /windows folder. So if you open up Nautilus and see you're in /home/jane, just go up two folders to / and you should see a whole bunch of folders (/boot, /etc, /home, /usr, /lib, /var...). One of those folders should be /windows, and it should have your Windows partition there.

---

### Post by nmastae on 2006-02-20
[QUOTE=aysiu]No. As I said before, you appear to have done everything correctly. The instructions I gave you were based on guesses, since I didn't get all three commands. James just wanted to be sure we were doing things right, so he asked for all three commands again.

 It may not appear as a "mounted disk," but it should appear in the /windows folder. So if you open up Nautilus and see you're in /home/jane, just go up two folders to / and you should see a whole bunch of folders (/boot, /etc, /home, /usr, /lib, /var...). One of those folders should be /windows, and it should have your Windows partition there.[/QUOTE]


Aysiu,

You have been so very generous with your time and knowledge and I thank you! 

I read your blog and really liked your essays! Based on your choices, I downloaded macosx.tar.gz but couldn't get it to install! (Invalid parameters, or something like that.) Which Mac-theme package do you recommend? What's the secret to getting it installed in Ubuntu?

I also did a file search for that one, and also Thunderbird, which I downloaded at the same time, but in each instance the searcher couldn't locate the files! So, my question about that is: when I down load a zipped file and choose the default unpacker, where do the original downloaded files end up? (I want to delete them so they won't clog up my nice clean OS!)

I see that you live in California. So do I! Where abouts are you, if you don't mind saying...

Best wishes,
Jane


PS Do you know of a way to keep the menus clean, short of installing U- and K- buntu on separate petitions?

Thanks again!

---

### Post by aysiu on 2006-02-20
[QUOTE=nmastae]
You have been so very generous with your time and knowledge and I thank you![/quote] You're welcome. Does that mean your Windows partition actually mounted properly?

> 
I read your blog and really liked your essays! Thanks. I just write about whatever pops into my head. 

> Based on your choices, I downloaded macosx.tar.gz but couldn't get it to install! (Invalid parameters, or something like that.) Which Mac-theme package do you recommend? What's the secret to getting it installed in Ubuntu? Well, if you download a Gtk theme in .tar.gz zipped format from a site like [http://www.gnome-look.org](http://www.gnome-look.org), you can just drag and drop it into the theme manager window, and it should install.

The macos.tar.gz zip file you downloaded may actually be an entire theme set, not just a Gtk theme. The Gtk theme basically determines how your window borders and controls look. The theme set may contain a Gtk theme, an icon theme, a set of wallpapers, and a login theme. So you need to unzip that file first and see what's inside. To unzip it in Gnome, just double-click it and then click **Extract**.

> 
I also did a file search for that one, and also Thunderbird, which I downloaded at the same time, but in each instance the searcher couldn't locate the files! So, my question about that is: when I down load a zipped file and choose the default unpacker, where do the original downloaded files end up? (I want to delete them so they won't clog up my nice clean OS!) They should unzip to the folder where the original .tar.gz was. For example, if you downloaded the .tar.gz to the desktop, the new folder should also unzip to the desktop. You may want to take a look at [https://wiki.ubuntu.com/ThunderbirdNewVersion](https://wiki.ubuntu.com/ThunderbirdNewVersion)

> 
PS Do you know of a way to keep the menus clean, short of installing U- and K- buntu on separate petitions? [This](http://ubuntuforums.org/showthread.php?t=77729) may help. I've never tried it out myself, though.

---

### Post by nmastae on 2006-02-20
[QUOTE=aysiu]You're welcome. Does that mean your Windows partition actually mounted properly?

 Thanks. I just write about whatever pops into my head. 

 Well, if you download a Gtk theme in .tar.gz zipped format from a site like [http://www.gnome-look.org](http://www.gnome-look.org), you can just drag and drop it into the theme manager window, and it should install.

The macos.tar.gz zip file you downloaded may actually be an entire theme set, not just a Gtk theme. The Gtk theme basically determines how your window borders and controls look. The theme set may contain a Gtk theme, an icon theme, a set of wallpapers, and a login theme. So you need to unzip that file first and see what's inside. To unzip it in Gnome, just double-click it and then click **Extract**.

 They should unzip to the folder where the original .tar.gz was. For example, if you downloaded the .tar.gz to the desktop, the new folder should also unzip to the desktop. You may want to take a look at [https://wiki.ubuntu.com/ThunderbirdNewVersion](https://wiki.ubuntu.com/ThunderbirdNewVersion)

<snip>

 [This](http://ubuntuforums.org/showthread.php?t=77729) may help. I've never tried it out myself, though.[/QUOTE]


Aysui,

Nope, I'll still in Windows, but will go over to Ubuntu again soon.

I think you are right, the file I downloaded is a whole package -- desktop, icons, etc. Do each of those folders go into a separate folder?

For the life of me I don't know where those original downloads have got to!
When the Firefox download manager opened up, I chose the default option, which was to open them with, in one instance, user/bin/file-roller, and in the  other, with the "archive manager". Do you have any idea where these files could be now?!

<snip>

Thanks for that menu-clean-up link. I think that for now I will just strive to become more familiar with Ubuntu; then, when I add Kubuntu, I'll be better able to ascertain the differences and know what I can, and can't tolerate...

Thanks also for the Thunderbird link. I will try to make that one work.

Best,
Jane

---

### Post by aysiu on 2006-02-20
[QUOTE=nmastae]
I think you are right, the file I downloaded is a whole package -- desktop, icons, etc. Do each of those folders go into a separate folder?[/quote] The icon .tar.gz and the Gtk theme .tar.gz can be dragged and dropped into the theme manager window. If there's a GDM them, you install it by going to System > Administration > Login Screen Setup > Graphical Greeter Themes. If you have a wallpaper, just right-click on the desktop and select "Add Wallpaper."

> 
For the life of me I don't know where those original downloads have got to!
When the Firefox download manager opened up, I chose the default option, which was to open them with, in one instance, user/bin/file-roller, and in the  other, with the "archive manager". Do you have any idea where these files could be now?! Maybe change the behavior to saving to the desktop instead of just opening with the archive manager?

> 
Thanks for that menu-clean-up link. I think that for now I will just strive to become more familiar with Ubuntu; then, when I add Kubuntu, I'll be better able to ascertain the differences and know what I can, and can't tolerate... Honestly, the additional items in the menus is only a slight annoyance. It's mainly a cosmetic issue.

---

### Post by nmastae on 2006-02-20
The icon .tar.gz and the Gtk theme .tar.gz can be dragged and dropped into the theme manager window. If there's a GDM them, you install it by going to System > Administration > Login Screen Setup > Graphical Greeter Themes. If you have a wallpaper, just right-click on the desktop and select "Add Wallpaper."

[COLOR="Blue"]
Wallpaper worked fine. Adding themes gives error message stating: invalid format. Trying to paste extracted gdm files directly into /usr/share/gdm/themes says I'm not authorized to add items to the folder. Also, my copy/paste command doesn't seem to work! (eg. copying the files to paste into the appropriate folder.)

Here's what the Readme file says:

gdm/ copy all the directory inside gdm to /usr/share/fdm/theme
gtk+metacity/ copy all the directory inside gtk to  /home/<user>/.themes
icons+cursor/ copy all the directory inside icons to /home/<user>/.icons 
splash/ cp all the file png into /usr/share/pixmaps/splash/
wallapaper/   set Normalli the wall[/COLOR]

Maybe change the behavior to saving to the desktop instead of just opening with the archive manager?
[COLOR="Blue"] Yes.
[/COLOR]
 I've enabled the private messaging on my Ubuntu Forums account. You can send me a "PM" right here on the forums.
[COLOR="Blue"]
Thank you. I'll contact you soon.[/COLOR]

 Honestly, the additional items in the menus is only a slight annoyance. It's mainly a cosmetic issue.

[COLOR="Blue"]Got it. 

Very tired. Time to take a break! :) 
[/COLOR]

---

### Post by aysiu on 2006-02-20
[QUOTE=nmastae]
Adding themes gives error message stating: invalid format. Trying to paste extracted gdm files directly into /usr/share/gdm/themes says I'm not authorized to add items to the folder.[/quote] I know that's what the README file says, but please do this instead for the GDM theme: Install it by going to System > Administration > Login Screen Setup > Graphical Greeter Themes

---

### Post by nmastae on 2006-02-20
[QUOTE=aysiu]I know that's what the README file says, but please do this instead for the GDM theme: Install it by going to System > Administration > Login Screen Setup > Graphical Greeter Themes[/QUOTE]
Okay, that works, but do I have to install the subfiles for each GDM theme, or whatever it is? (5 separate theme folders, each with 6-7 subfiles.)

---

### Post by aysiu on 2006-02-20
[QUOTE=nmastae]Okay, that works, but do I have to install the subfiles for each GDM theme, or whatever it is? (5 separate theme folders, each with 6-7 subfiles.)[/QUOTE] I'm not sure what you mean by the subfiles. The GDM theme is one .tar.gz file that gives you a theme for the login screen.

Here's a GDM theme I like to use:
[http://www.gnome-look.org/content/show.php?content=15994](http://www.gnome-look.org/content/show.php?content=15994)

See? One file.

Are the other files the Gtk/metacity themes? Are they icon themes? Actually, can you link to where you downloaded the initial .tar.gz?

---

### Post by nmastae on 2006-02-20
[QUOTE=aysiu]I know that's what the README file says, but please do this instead for the GDM theme: Install it by going to System > Administration > Login Screen Setup > Graphical Greeter Themes[/QUOTE]
Actually, it didn't work. New themes not showing up in the Themes window. Unless those were login screens. Subfiles didn't install because they are not tar.gz files

---

### Post by aysiu on 2006-02-20
Try this bundle:
[http://www.gnome-look.org/content/show.php?content=28686](http://www.gnome-look.org/content/show.php?content=28686)

These two files inside can definitely be dragged and dropped into the Theme Manager window:
mac-osx-controls.tar.gz
mac-osx-window.tar.gz

---

### Post by nmastae on 2006-02-20
Here's where the macosx.tar.gz file came from:
[http://www.gnome-look.org/content/show.php?content=19714](http://www.gnome-look.org/content/show.php?content=19714)

---

### Post by aysiu on 2006-02-20
[QUOTE=nmastae]Here's where the macosx.tar.gz file came from:
[http://www.gnome-look.org/content/show.php?content=19714](http://www.gnome-look.org/content/show.php?content=19714)[/QUOTE] That's weird. When I click **download** on that page, I just get taken to another page, but no download starts...

---

### Post by nmastae on 2006-02-20
[QUOTE=aysiu]Try this bundle:
[http://www.gnome-look.org/content/show.php?content=28686](http://www.gnome-look.org/content/show.php?content=28686)

These two files inside can definitely be dragged and dropped into the Theme Manager window:
mac-osx-controls.tar.gz
mac-osx-window.tar.gz[/QUOTE]

When I did this the mac themes I'd installed previously disappeared!
As did my particular desktop.

In fact, I didn't see the new themes lisited!

J.

---

### Post by aysiu on 2006-02-20
That's weird.

Maybe try closing the theme manager and then re-opening it?

---

### Post by jamesr on 2006-02-20
Hi nmastae

 As Asyiu stated
> It looks as if you followed the directions correctly!

So... you should be able to see your Windows partition in the /windows folder. Go ahead and open up Nautilus (in Gnome) or Konqueror (in KDE) and navigate to the /windows folder.


Looks oK 

Sorry I could get back online more quickly but you in Aysiu's capable hands so no problems and that was the reasoning behind asking for the files. 

aysiu said it prefectly
> No. As I said before, you appear to have done everything correctly. The instructions I gave you were based on guesses, since I didn't get all three commands. James just wanted to be sure we were doing things right, so he asked for all three commands again.



Because you had done a rebuild, something may have set up slightly differently during the rebuild.BUT the main thing that you are up and working.

Also we were posting our replies at a similar time , and I did not see asyiu's until I relogged on tonight.

---

### Post by nmastae on 2006-02-20
I had that problem too. Then I clicked on the GNU (?) Icon in the middle of that screen and the download started right up. 

I did install this one <28686-mac-osx-bundle.tar.gz> and it looks pretty good.
BTW, the instructions accompanying that bundle are very clear.

How do I delete a theme I don't want (in this case another Mac reference that's not very good.)

J.

---

### Post by jamesr on 2006-02-20
Hi aysiu,

Thanks for following through when I could not get on-line . As I commented, we were posting at a similar time and if I had not changed my mind and deleted my original post it would have been earlier.

Also you were able to help on the other points where I would have been no use .

---

### Post by nmastae on 2006-02-20
Thanks, Jim. The /Windows tweak worked PERFECTLY and I'm deeply grateful to you both. 

I've had a fun day working with Ubuntu. My first day, really. I like it a lot better than Suse, which I inherited with this P3 box but never really used. The Ubuntu community makes all the difference!

It's also fun to have it looking something like a Mac with OSX! :)

Jane

---

### Post by nmastae on 2006-02-21
A few more questions:
 
1) How to remove a theme I don't want?

2) How to remove an erroneous entry in the Themes menu? I have the Mac-OS Controls in the Window Border screen (and also where they belong, in the control screen).

3) My desktop background picture disappears everytime I tweak something related to this Mac emulator package. The entries I'd made previously even disappear from the Wallpaper setup box!

4) How do I install the icon package I just downloaded?

Over and out.

J.

---

### Post by aysiu on 2006-02-21
[QUOTE=nmastae]A few more questions:
 
1) How to remove a theme I don't want?[/quote] Go to /home/jane/.themes and delete the appropriate theme. You can also remove them from the Theme Manager.

> 
2) How to remove an erroneous entry in the Themes menu? I have the Mac-OS Controls in the Window Border screen (and also where they belong, in the control screen). That's not erroneous, believe it or not.

> 
3) My desktop background picture disappears everytime I tweak something related to this Mac emulator package. The entries I'd made previously even disappear from the Wallpaper setup box! That's weird. I don't know what that is.

> 
4) How do I install the icon package I just downloaded? Just drag and drop the .tar.gz into the Theme Manager window.

**Edit**: I just downloaded the bundle you were originally looking at (GnoMac), and I see what the problem is. First of all, all the themes in there are not .tar.gz files--they're unzipped folders, and within those folders are more folders (so there's not *one* GDM theme in the GDM themes folder... there are five of them).

---

### Post by aysiu on 2006-02-21
[QUOTE=aysiu]
**Edit**: I just downloaded the bundle you were originally looking at (GnoMac), and I see what the problem is. First of all, all the themes in there are not .tar.gz files--they're unzipped folders, and within those folders are more folders (so there's not *one* GDM theme in the GDM themes folder... there are five of them).[/QUOTE] The solution: just zip the folders. Then you can install the GDM themes through the Login Screen Setup (see screenshots) and you can drag and drop the Gtk/Metacity themes to the Theme Manager window.

---

### Post by nmastae on 2006-02-21
Go to /home/jane/.themes and delete the appropriate theme. You can also remove them from the Theme Manager.
[COLOR="Blue"]
I don't have a home/jane/.themes folder! Could I have been putting these in the wrong place?![/COLOR]

[COLOR="Purple"]Re. Installing new icons... (File is .tar.gz)[/COLOR]
 Just drag and drop the .tar.gz into the Theme Manager window.

[COLOR="Blue"]I did this, but the icons don't show up in the Theme Preferences/Icons tab. Where else would I find them?[/COLOR]

**Edit**: I just downloaded the bundle you were originally looking at (GnoMac), and I see what the problem is. First of all, all the themes in there are not .tar.gz files--they're unzipped folders, and within those folders are more folders (so there's not *one* GDM theme in the GDM themes folder... there are five of them).
[COLOR="Blue"]
And they're already extracted? And thus useless for our purposes?[/COLOR]

[COLOR="Blue"]J.[/COLOR]

---

### Post by aysiu on 2006-02-21
[QUOTE=nmastae]
I don't have a home/jane/.themes folder! Could I have been putting these in the wrong place?![/quote] The .themes folder is a hidden folder. If you go to Places > Home and then press Control-H you'll be able to see all the hidden folders.

> 
And they're already extracted? And thus useless for our purposes? Ah, but they can be re-zipped. See the screenshots I put in my last post.

---

### Post by hikmat on 2006-03-09
Hello,

I read the replies and followed the instructions, and was able to mount my fat32 windows partition. Thanks!

Only difference I was not allowed to do kwrite as root. So I had to do the editing of the fstab file in vi. It is a pain, but once you get used to working in it, it is not that bad.

One of the good things about the Ubuntu/Kubuntu forums is that the posts are a great help in learning new things about the OS.

Keep up the good work!

---

### Post by aysiu on 2006-03-09
I've found *nano* a bit more "user-friendly" than *vi*.

---

