---
title: "NTFS-Config Side Effect: All Files Are Executable"
date: 2011-06-05
forum: Desktop Environments
---

### Post by irahwan on 2011-06-05
I just installed Ubuntu 11.04 with Unity.

Although Ubuntu mounts my NTFS partition once I open the file explorer, I wanted to see my NTFS partition from the command line as soon as I boot up. So I installed the "NTFS Configuration Tool" (ntfs-config).

Now, the NTFS partition is mounted already when I start Ubuntu. But all files are now set to "executable". This causes two annoyances:

1- In the Terminal, all files are colored bright green, and folders have green highlight, which is visually very annoying.

2- When I double click on some files (e.g. txt files), I get the message: 

[CENTER][FONT=System]Do you want to run "x.txt" or display its content? "x.txt" is an executable text file.[/FONT]
[/CENTER]

Is there any way I can avoid this? Help would be very much appreciated.

---

### Post by Utrader on 2011-06-14
Hi,
 
I need help to create an "auto install" (at boot or after login) for the "ntfs-config" package everytime I start Ubuntu 11.04.
 
You need to confirm the installation ('sudo ntfs-config') everytime with your password  (sudo password) so I do not think you just can add it the "easy way" (System –> Preferences –> Startup Applications).
 
I'm a complete newbe so a step-by-step instruction would be much appreciated!
 
Many thanks!

---

### Post by coffeecat on 2011-06-14
To both of you, my advice is: ntfs-config was a good idea when first developed a few years ago but has a number of significant drawbacks, and can sometimes do the most extraordinary things. Use with the utmost caution. It is not an "official" Ubuntu package.

@irahwan, my guess is that ntfs-config has set the exec option in /etc/fstab. The problem with Microsoft filesystems (such as NTFS) in Linux is that they do not support Linux permissions, so permissions have to be set globally with the mount options. Which means that all files on your NTFS partition have to be executable or all files non-executable.

Open a terminal (ctrl-alt-T is a useful shortcut for this) and post the output of this command:

```
cat /etc/fstab
```

You can copy and paste that by highlighting the output with the mouse, right-click -> copy and then pasting it into your post.

@Utrader, welcome to the forum, but in future it's better if you start your own thread. Tagging onto someone else's can get very confusing if help is still being given to the OP.

But to your question. You only run ntfs-config once to configure partitions to be mounted automatically on boot. You don't run or install ntfs-config every time you bootup. What exactly are you trying to achieve?

---

### Post by FormatSeize on 2011-06-14
The chmod command man page should tell you how to make the files such that they aren't executable.
The command 
```

chmod 755 filename
```
makes the file executable, and 
```
chmod 600 filename
```
makes the file non-executable.

---

### Post by Morbius1 on 2011-06-14
chmod and chown don't work on ntfs or fat32 because there are no linux permissions or linux ownership bits to set.

You can only achieve this sort of thing with a dmask / fmask option in fstab or in an explicit mount.

---

### Post by Utrader on 2011-06-14
Hi,

Thank you all for your answers!

Cofeecat:
........................................
OptiPlex-755:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda5 :
UUID=be5790c8-d0fb-46d8-93c0-f351be696a0b    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdb5 :
UUID=1716A2A8B49B49B1    /media/FILMER-1Tb    ntfs-3g    defaults,nosuid,nodev,locale=sv_SE.UTF-8    0    0
#Entry for /dev/sda1 :
UUID=02547D39547D3091    /media/sda1    ntfs-3g    defaults,locale=sv_SE.UTF-8    00
#Entry for /dev/sda6 :
UUID=37781d32-9066-4110-ac54-1d76f6d843c4    none    swap    sw    0    0


OptiPlex-755:~$ 
..................................................
What I'm trying to achieve is to use luckybackup to sync two hdd drives (one ntfs and one etx4) connected via USB. The transfer speed to the NTFS hdd is very low (29kb/s) but if I open a terminal (works every time) and write 'sudo ntfs-config' the speed goes up to 30Mb/sec. 
That is why I would like to automaticly execute 'sudo ntfs-confog' every time I start my pc. 

To be honest I tried to start a new thread but I could not find the answer how to do that :) I red the FAQ, I looked under every head line and thought I would find under "New Posts" but not, then I found this thread and a "reply" button :) 

I told you I'm a newbe on this.

---

### Post by coffeecat on 2011-06-14
> **Utrader said:**
> The transfer speed to the NTFS hdd is very low (29kb/s) but if I open a terminal (works every time) and write 'sudo ntfs-config' the speed goes up to 30Mb/sec. 

:shock:

That is about the weirdest thing I think I've come across on this forum. I don't disbelieve you, far from it, it's just very.... weird. :-k

ntfs-config's one and only function is to write mount lines to /etc/fstab for ntfs-formatted partitions. However, it lists as dependencies some python packages and udev. I just wonder if by starting it up, it is having a quite unintended and unexpected effect on luckybackup.

Since luckybackup is a frontend for rsync (is it a GUI?) I would suggest that it might be worth seeing if other rsync frontends will run without this issue. There are several in the repositories. Just search with the string "rsync" in Synaptic.

I was hoping that Morbius1, who has made a valuable contribution to the thread and who knows a thing or three about matters NTFS, might add a comment. :)

---

### Post by Morbius1 on 2011-06-14
Actually I was waiting for your explanation of the ntfs-config and transfer speed thing because I sure don't have one.

I'm still trying to figure out how LuckyBackup can be used with an NTFS partition. The last time I used it it couldn't create an archive so it's a file to file backup. Move a file to an ntfs partition and you just lost the original permissions and ownership. I guess it depends on what you're backing up.

Anybody wants to know how to mount an ntfs partition so all the folders are executable and all the files are not - I'm your man. As for the rest of this all I can offer is comic relief ;)

---

### Post by Utrader on 2011-06-14
I have tried 'Grsync', 'backuppc' and 'luckybackup', same result (around 29kb/s). 
It was first after I came across the 'ntfs-config' package which gives write access to ntfs partitions that the speed increased to around 29 Mb/sec.
 
I then tried to sync the hdd another day and the speed quickly droped. I then "restarted" ntfs-config (terminal -> $ sudo ntfs-config) and the speed got up to 30Mb/sec again.
 
If I uses the ntfs hdd as source (etx4 as destination) the speed is good all the time (no need to use the ntfs-config) but if I switch and uses the etx4 as source and nfts as destination then the speed quickly drops after a while.

---

### Post by coffeecat on 2011-06-14
One other app to try is gadmin-rsync. Maybe the problem is rsync-ing to an NTFS partition. I really don't know. Try a simple drag and drop ext4 > NTFS. What sort of speeds do you get?

> **Morbius1 said:**
>  As for the rest of this all I can offer is comic relief :wink:

Perhaps we can set up a double-act. I'm happy to be the stooge and you can get all the punch-lines. :razz:

---

### Post by Utrader on 2011-06-14
Also tried that, drag n drop ext4>ntfs, same thing.
 
Is it hard to create a script which performs "sudo ntfs-config" at login, I think that would be a workaround.

---

### Post by Utrader on 2011-06-14
Coffecat:
Thanks for the tip, gadmin-rsync, I will try that tomorrow.

---

### Post by irahwan on 2011-06-14
Thanks for your help coffeecat. I should have know that ntfs-config had issues.

I am now avoiding it. So instead, I edited my fstab directly, using dmask and fmask to ensure neither files nor directories are executable. Here's what my fstab looks like. Notice the mount command for my NTFS drive "/media/PERSONAL"

```
proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda2    /host    fuseblk    defaults,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096    0    0
/dev/sda5    /media/PERSONAL    ntfs-3g    dmask=000,fmask=111,uid=1000,locale=en_US.UTF-8    0    0
/host/ubuntu/disks/root.disk    /    ext4    loop,errors=remount-ro    0    1
/host/ubuntu/disks/swap.disk    none    swap    loop,sw    0    0

```Now, to my surprise, when I boot, while all files are not executable (-rw-rw-rw-), directories are still executable for some reason. Any idea why?

---

### Post by coffeecat on 2011-06-14
> **Utrader said:**
> Also tried that, drag n drop ext4>ntfs, same thing.

That is very significant. You ought to be  getting a speed of somewhere between about 10-40 MB/Sec depending on hardware factors. Even with an old 2½" laptop drive in an USB enclosure and hence slow, copying ext4 > NTFS I am getting a steady 10.5 - 11.0 MB/Sec. I don't know whether Morbius1 has a view on those NTFS mount options, but getting proper transfer speeds by invoking ntfs-config is a bit like getting a faulty freezer to work by opening the back door in winter. It's the wrong approach.

I'm sorry, but I don't have any ideas at the moment as to why your transfer speeds are wrong.

---

### Post by coffeecat on 2011-06-14
> **irahwan said:**
> Now, to my surprise, when I boot, while all files are not executable (-rw-rw-rw-), directories are still executable for some reason. Any idea why?

No, but I know a man who does. :wink:

> **Morbius1 said:**
> 
Anybody wants to know how to mount an ntfs partition so all the folders are executable and all the files are not - I'm your man. As for the rest of this all I can offer is comic relief ;)

---

### Post by Morbius1 on 2011-06-14
> **coffeecat said:**
> No, but I know a man who does. :wink:
I'll give it a shot:

By using "defaults" in the fstab line that ntfs-config creates it sets a parameter of umask=000.

umask represents the permissions that you want to take away and it will do that for every folder and file in the partition:

1 - removes execute
2 - removes write
4 - removes read
0 - removes nothing - full access

And they're additive so a "7" for example removes all permissions ( 1+2+4 = 7 )

When you set umask = 000 you are setting r/w/x to every file and every folder. dmask and fmask separates umask into into it's directory ( dmask ) and file ( fmask ) components.

So you set dmask=000 which makes all folders executable which for a folder means you can open it to see what's inside. You set fmask=111 which turns off the execute bit for all files.

[COLOR=Blue]**EDIT:**[/COLOR] Just in case you're wondering. Each position in the umask, dmask, fmask represents a different kind of user:

1st position = owner
2nd position = group
3rd position = everyone else

---

### Post by Utrader on 2011-06-15
Many thanks for clearing that out.
 
So what do I do and mostly how do I do it  :)

---

### Post by Utrader on 2011-06-15
Should I also try to edited my fstab directly?
 
How do I do that, what tools do I use?
 
A step-by-step instructions would be much appreciated.
 
Then I have to remove the ntfs-config package, right?

---

### Post by coffeecat on 2011-06-15
@Utrader, I don't think anyone suggested you edit fstab, but for the record the command is:

```
gksudo gedit /etc/fstab
```

But proceed with care. The command gksudo gives you root powers to edit that system file, and if you make an error you could conceivably make the system unbootable. Until you repair it from a live CD, that is.

And removing the ntfs-config package is not really necessary. If it's not running, it's not doing anything. I think you need to find out why your system is only copying files from ext4 to NTFS at about 29KB/s. (I think that might be KB, not Kb. If it was Kb, you'd be able to count the electrons as they went past! :wink:) Since you were getting that speed with a normal drag and drop, then rsync-ing with those packages is not the issue. And although it wouldn't be a good idea to invoke ntfs-config as a workaround, the fact that it seems to spur the copy process into action must give a clue as to what is wrong, but I can't think what this might be.

I think it would be helpful to you to start your own thread. The title of this one is "NTFS-Config Side Effect: All Files Are Executable" and is not going to attract people who might know what to do. Choose a thread title which describes the problem succinctly. I'd suggest: "Very slow copy/rsync speeds ext4 to NTFS". And describe what happens when you invoke ntfs-config. You may very well get someone who suggests starting ntfs-config in a startup script as you originally wanted but I think this is a very bad idea. It doesn't get to the bottom of what should be a fixable issue.

As to how to start your own thread. Find a subforum which would be appropriate. It's a bit of a catch-all but I would suggest [General Help]("http://ubuntuforums.org/forumdisplay.php?f=331"). If you click that link, you'll see a clickable "New Thread" button near the top left and also near the bottom left.

Good luck!

---

### Post by Utrader on 2011-06-15
Many thanks for all your answers and support, great forum!
 
I will try the other way around  :)
 
I'm going to try the program "Ext2Read" ([http://sourceforge.net/projects/ext2read/](http://sourceforge.net/projects/ext2read/)) for Windows. With that program I should be able to read from an ext4 hdd from Windows. If that seems to work the way I hope I will then format my ntfs hdd to ext4. 
 
After that I'm sure all the backup programs I have tried for Ubuntu will work the way I expect.

---

### Post by coffeecat on 2011-06-15
> **Utrader said:**
> Many thanks for all your answers and support, great forum!
 
I will try the other way around  :)
 
I'm going to try the program "Ext2Read" ([http://sourceforge.net/projects/ext2read/](http://sourceforge.net/projects/ext2read/)) for Windows. With that program I should be able to read from an ext4 hdd from Windows. If that seems to work the way I hope I will then format my ntfs hdd to ext4. 
 
After that I'm sure all the backup programs I have tried for Ubuntu will work the way I expect.

Good luck with that. I'm sorry that writing to a NTFS partition has been problematic for you. This is most unusual. If you format the drive ext4, you will immediately have permissions problems in Ubuntu unless you set appropriate mount options in /etc/fstab or do some chmod and chown commands on the ext4 filesystem. Personally, I prefer the latter, but there are plenty of people to help with either way.

---

### Post by Utrader on 2011-06-15
Hi,
 
Many thanks for your reply!
 
So, next question:
How do I do some chmod and chown commands on the ext4 filesystem?
 
I have not done so for the ext4 hdd that I have so that might be a reason for low transfer speed or?

---

### Post by coffeecat on 2011-06-15
> **Utrader said:**
> I have not done so for the ext4 hdd that I have so that might be a reason for low transfer speed or?

I thought you were only getting low transfer speeds to NTFS. If you are getting low transfer speeds to ext4 then something is seriously wrong somewhere and no amount of chmodding and chowning is going to help.

This is getting unfair on the OP. Thread hijacks are frowned on in this forum. If you start your own thread and pm me with the link, I'll mosey over and help you with the chmod and chown bit, but I can't say that I can help with low transfer speeds.

---

### Post by Utrader on 2011-06-15
New thread for this issue:
**"Very slow copy/rsync speeds ext4 to NTFS"**
 
[http://ubuntuforums.org/showthread.php?p=10941635#post10941635](http://ubuntuforums.org/showthread.php?p=10941635#post10941635)
 
All support and knowledge are much appreciated!

---

### Post by Micha401 on 2011-06-15
[QUOTE=Utrader;10938617]Hi,


UUID=1716A2A8B49B49B1    /media/FILMER-1Tb    ntfs-3g    defaults,nosuid,nodev,locale=sv_SE.UTF-8    0    0

Hi,
try instead
UUID=1716A2A8B49B49B1    /media/FILMER-1Tb    ntfs-3g    defaults,**noexec**,nosuid,nodev,locale=sv_SE.UTF-8    0    0
in your fstab.
BTW., same thing happens for every USB Sick, which comes normally with FAT32.
Remove exec bit via
chmod -R a-x topdir && chmod -R a+X topdir
The last command sets only directories back to exec. This can be configured as a Nautilus-Action, so a rightclick onto topdir is sufficient.

---

