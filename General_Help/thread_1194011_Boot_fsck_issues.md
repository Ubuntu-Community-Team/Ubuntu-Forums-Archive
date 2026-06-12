---
title: "Boot fsck issues"
date: 2009-06-22
forum: General Help
---

### Post by Mikael P. on 2009-06-22
Hello forum,
I was wondering if anyone could shed some light on this.
Almost everytime I boot ubuntu I get something about read only file system / boot partition. Where it wants me to run fsck manually.

The start of the error message goes like this:
> An automatic file system check (fsck) of the root file system failed. A manual fsck must be performed. etc. etc.Then I just have to run it myself and say yes to the fixes it wants to do.

My question is why? There were no bad shutdowns or crashes.

One theory of mine is the fact that Vista has problems starting up when the machine is cold, but Ubuntu has none of those issues. So maybe it's something in the background that Ubuntu doesn't care that much about but still bothers it?


[/start rant]On another note, could anyone point me to good resources to start learning about linux? The intro pdf, ubuntupocketguide was a bit silly. It like so many other intro courses start with telling you to go to menu x and change y. But the moment something fails or you need to do something marginally advanced, well hello scripting.
I am no programmer but did play around with some scripts in Irix many years ago. But it is quite overwhelming the stuff you have to do to get most things working in Ubuntu. [/end rant]

---

### Post by dazman19 on 2009-06-22
I think it has a thing like every 30 reboots or so it will run the check.

I think in the /etc/fstab there are 2 numbers (in my case 0's). These have something to do with it. 

/dev/sdc1       /data                   ext3    defaults        0       0

Taken from: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
< 5th and 6th columns: Dump and fsck options >

Dump and, uh, what options? Well, dump is a backup utility and fsck is a filesystem check utility. I won't discuss them in great length here (they would both need their own tuXfile), but I'll mention them, because otherwise you'd spend the rest of the day wondering what on God's green Earth do these things mean.

The 5th column in /etc/fstab is the dump option. Dump checks it and uses the number to decide if a filesystem should be backed up. If it's zero, dump will ignore that filesystem. If you take a look at the example fstab, you'll notice that the 5th column is zero in most cases.

The 6th column is a fsck option. fsck looks at the number in the 6th column to determine in which order the filesystems should be checked. If it's zero, fsck won't check the filesystem.

Hope it helps...

As for your rant.. I did and sometimes still do share your pain. But I cant dream of switching back to windows with the level of malware/virus and wot not these days its a joke.. 

It comes with time but great packages like synaptic make things worthwhile. The system is WAY more customizable than a win NT system and hence this makes it more complex. To top it off it can be more difficult to get help. I have used unix type systems since about 2002/2003 and believe me it is so much easier to find help these days than back then. :D

---

### Post by Mikael P. on 2009-06-22
hmm. Not sure I understood that. This is what my fstab looks like:

> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=e1ac52e8-5cc0-492b-a5bb-957e99b38722 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=e5af7747-8f48-4771-a852-0c3ce7f02f82 /home           ext3    relatime        0       2
# swap was on /dev/sdb4 during installation
UUID=045fab61-7ef3-47df-bae6-837b9879c7cc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

But the thing is that this is no ordinary scheduled check. There are big red letters saying FAILED. So I gather something is amiss?

---

### Post by Mikael P. on 2009-06-22
As towards your edit. It seems really great this forum (and other places I've bumped into).
But when you just want to watch something by using flash and the help files to get it working...

Maybe you know about Alsa vs. PulseAudio? I managed to get some sound out of the system by installing some Alsa drivers. This was during the install setup phase and I was just getting used to Ubuntu. I did some apt-gets and what-nots. But it worked.
Now I lost the sound on flash pages but still have it when I play mp3's or listen to internet radio.

---

### Post by dazman19 on 2009-06-22
Sorry Mikael

I cant answer why, I dont really have enough information on the fixes it wants to do. 

That failed check doesnt sound good. If you do run the fixes does it go away? or is it there even after you have ran fsck manually?

Dont get me started on ALSA. I have had a few problems myself. 

Its possible your system could be using a mix of pulse audio and ALSA. Some apps accessing ALSA and some accessing pulseaudio. And due to your sound preferences only either/or works.. I did read a post when I was having problems about killing the pulse audio process and getting everything to run on ALSA. The outcome was to kill pulse audio, then edit my sound preferences so the default mixer was Alsa and I fiddled with the devices. I used Master/front etc and eventually it came right. 

But in all honesty I think a separate thread about this would be in order?

---

### Post by Mikael P. on 2009-06-22
No worries. Thanks for your help anyway! Yes, it does bother me. I get this failed boot often, almost every day. I hardly restart during the day, so it's not that I run into the 30 times limit.
Could I supply some other info to help out?

Indeed I think a new topic would be more suitable. It's just that there are so many things I wonder about.

---

### Post by Herman on 2009-06-22
> Almost everytime I boot ubuntu I get something about read only file system / boot partition. Where it wants me to run fsck manually.

The start of the error message goes like this:
                                                      [quote]An automatic file system check (fsck) of the root file system failed. A manual fsck must be performed. etc. etc.                      Then I just have to run it myself and say yes to the fixes it wants to do.

My question is why? There were no bad shutdowns or crashes.[/quote]My guess, (from the information provided), is that either 

[LIST]
[*]you have some file system problem and although you're running fsck, you're not running your file system check with the right options to be able to clear it
[/LIST]
or 

[LIST]
[*]you have a hard disk that's on its way out
[/LIST]
 
If you have an ext series file system, try running 'sudo e2fsck -C0 -p -f -v /dev/sda#',```
sudo e2fsck -C0 -p -f -v /dev/sda2
```                                                                                                                                                                                                                                                   Where: sda2 is the ext* partition to be checked. 
With these options, e2fsck can solve quite a large number of file system problems, even some quite severe ones.

If that doesn't do it, it will at least give you some feedback to tell you what to do next. If you think you might want advice, it would be a good idea to record the exact message by copying and pasting, then someone here will be able to interpret it for you.


A 'bad block' is an area of your hard disk where the material is losing it's ability to retain a magnetic field and thus store data reliably. There are spare sectors in your hard disk when it is new, which the hard disc will swap out silently when badblocks develop due to imperfections and deterioration of the materials. It's only after those spare sectors have been all used up that bad blocks start to become apparent to the file system. When that starts to happen, either your hard disk is getting close to the end of its useful life or it is failing prematurely.

The command 'sudo badblocks -sv /dev/sda2' or whatever partition number you have, is for checking your hard disk for bad blocks. It can take quite some time, especially if have a big hard disk and you decide to check the entire hard disk at once. In my opinion it's better to check one partition at a time.
```
sudo badblocks -sv /dev/sda2
```Where: /dev/sda2 is the partition to be checked. Replace this number with your own partition number which you should know from reading the output from 'sudo fdisk -lu', or by looking with Gnome Partition Editor.

If your hard disk has bad blocks, you will be given lots of numbers. Your hard disk probably should be replaced very soon!!!
Here's what you should see when it's finished if your hard disk has passed,
```
Checking blocks 0 to 12908226
Checking for bad blocks (read-only test):done
Pass completed, 0 bad blocks found.
``` . . . (or something like that).

Regards, Herman :)

---

### Post by Herman on 2009-06-22
I forgot to say that you should run these commands from your Ubuntu Live CD, (or any Live CD), so that you are not running them on any file system while it is mounted.

---

### Post by Mikael P. on 2009-06-22
Thanks for your extensive post Herman. Would these checks work on NTFS partitions too? As I am just about to migrate to Ubuntu most of my partitions are from Windows.

How do I go about copy n pasteing the text I get when these fsck errors occur? As I am in a text only command promt environment.

---

### Post by Herman on 2009-06-22
> Thanks for your extensive post Herman. Would these checks work on NTFS partitions too? As I am just about to migrate to Ubuntu most of my partitions are from Windows.
Partitions containing NTFS file systems are best checked by Windows. The last time I tried, Linux couldn't actually run a file system check in an NTFS partition, but can put a 'dirty' flag in the NTFS superblock to tell Windows to do it next time Windows boots up.

If your Windows system is working, an easy way is to schedule CHKDSK to run next time you reboot Windows XP, you can go 'My Computer',-->'Local Disk (C:), (or whatever drive you want to have checked), and right-click on 'Properties'. 
Open the 'Tools' tab, and in the 'Error Checking' box, click the 'Check Now' button.
A 'Check Disk' window will open. Make your desired settings, and the disc check will be performed on your next reboot.
If Windows won't boot, the other way is to use your Windows XP 'Installation Disc', and open a  a [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm"), and run CHKDSK /F for a quick check, or CHKDSK /R for a more thorough check. 

If you're migrating to Linux, it will probably be best to eventually move your data to a partition which is formatted with a Linux file system. You don't have to do it right away, maybe a little at a time. Linux doesn't damage the NTFS file system, but all file systems like a file system check once in a while, even just with regular use.
> How do I go about copy n pasteing the text I get when these fsck errors occur? As I am in a text only command promt environment. 	
I meant for you to run your file system check from your Ubuntu Live CD. 
You can boot your Ubuntu 'Desktop' Live/Install CD and open a terminal in that and if you want to you can copy and paste commands from Ubuntu Web Forums via Firefox web browser. Just check that the commands are right for your system first, often things like partition numbers are given in a command and you should check that your partition numbers aren't different. If they are, you should modify the command before you press enter.
The Live CD features Gnome Partition Editor, (GParted). If you want, you can run a file system check from GParted too. Just right-click on any unmounted partition and click 'check', and click 'apply', then 'apply once more to confirm.

One good file system check should fix it, the file system check that runs automatically is a safe one, and is good enough for most regular maintenance, but sometimes there's a small problem it can't quite get over, and you need to run a more powerful file system check. Once you actually fix the problem, it probably will never re-occur, and you'll only have a breif check once in every 30 boots, unless you run a file system check yourself (volutarily), prior to that.

Regards, Herman :)

---

### Post by Mikael P. on 2009-06-23
I see, well I did a thorough check of all the windows partitions very recently.
But I think I bumped into why this might be happening;
Sometimes the graphic interface stops working in a fashion when I am using Ubuntu. Every option box or system preference/administration window I open is blank. Just the close X in the upper right corner is left. But the OS is still running, nothing else is complaining.
Then when I reboot I get the fail, run fsck manually message. It booted fine this morning, so I thought maybe they are related?

---

### Post by dcstar on 2009-06-24
> **Mikael P. said:**
> 
........
Sometimes the graphic interface stops working in a fashion when I am using Ubuntu. Every option box or system preference/administration window I open is blank. Just the close X in the upper right corner is left. But the OS is still running, nothing else is complaining.
......

Turn off all display effects.

---

### Post by Mikael P. on 2009-06-24
But, what would that do?
remove the occasional black windows?

I prefer the basic one, but then transparency and 3D acceleration goes too. As I use the system for graphics that is not really working.

---

