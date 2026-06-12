---
title: "How do I mount?"
date: 2005-03-29
forum: Desktop Environments
---

### Post by JenniferDry on 2005-03-29
How do I mount a partion?
I tried "sudo mount hda5 " but it says that the mount point does not exsist.
Here is the list from fdisk -l
/dev/hda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/hda2            6375       22868   132488055    f  W95 Ext'd (LBA)
/dev/hda5            6375       12782    51472228+   b  W95 FAT32
/dev/hda6           12783       12846      514048+  82  Linux swap / Solaris
/dev/hda7           12847       19221    51207156   83  Linux
/dev/hda8           19222       22868    29294496   83  Linux

---

### Post by bored2k on 2005-03-29
Chances of you succesfully mounting a drive with the command your using are as big as 50 Cent getting mad  @ jdodson's [We Invented Rap Music](http://www.pdxbands.com/mp3s/roy_weinventedrapmusiclive.mp3) track and firing back with Piggy Bank pt. 2 ..

[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

---

### Post by JenniferDry on 2005-03-29
david@ubuntu:~/Desktop$ sudo mkdir /media/windows
david@ubuntu:~/Desktop$ Mount Windows partition
bash: Mount: command not found
david@ubuntu:~/Desktop$ mount Windows partition
mount: only root can do that
david@ubuntu:~/Desktop$ sudo mount Windows partition
mount: mount point partition does not exist
david@ubuntu:~/Desktop$

---

### Post by bored2k on 2005-03-29
Try
1. For your /dev/hda1 NTFS
> sudo mkdir /media/windows; sudo mount /dev/hda1 /media/windows -t ntfs -o umask=0222
2. For your /dev/hda5 FAT32
>  sudo mkdir /media/windows2; sudo mount /dev/hda5 /media/windows2 -t vfat -o umask=000

[http://www.ubuntuguide.org](http://www.ubuntuguide.org) will really help you with most of the Ubuntu simple -yet annoying- hiccups .

* edit 1*> Welcome to the forums by the way  :mrgreen: .
* edit 2 *> Just so you know, Linux is case sensitive, so Windows is not windows nor wIndows, etc .

---

### Post by JenniferDry on 2005-03-29
I tried mounting my linux partion.
Doesn't work.
I am trying to set my fstab. I saw instructions in the guides for mounting fat and ntfs but not ext partions.
I tried copying the vfat one and changing the vfat to ext3 but I think there is a problem with the umask part.
This will be my last question for a week

/dev/hda7       /media/mepis    ext3    umask=000       0       0

---

### Post by digby on 2005-03-30
The way the mount command works isn't to complicated once you've used it a couple of times. After you get that first successful mount, you'll be fine. You said that you tried to mount your linux partition, but unless you have multiple distros, Ubuntu should mount all of it's partitions (/, /home, and swap on my machine) at boot time.

To play with the mount command, just remember the proper syntax:

#mount /device/location /mount/location options

/device/location is the physical drive *and* the partition number.  
/mount/location is where you want to access the drive from in your filesystem
options include telling the mount command what type of filesystem that you want to mount

For example, if your primary hard drive is on IDE channel 1, it is called hda. The first partition on hda is labeled hda1. For this example, we will assume this is a Windows XP partition formated with the NTFS filesystem, and we want to mount it at /media/windows. You could just as easily put it at /some/other/directory/anywhere if you made dir first.

So the command would be:  $sudo mount /dev/hda1 /media/windows -t ntfs

If you don't know what type of filesystem you are mounting, you can use "-t auto" and it will figure it out for you.

So all that's left to you is to figure out what your partitions are called.

General layouts for drives are:

IDE 1 Master     hda
IDE 1 Slave       hdb
IDE 2 Master     hdc
IDE 2 Slave       hdd
SATA 1               sda
Floppy               fd

I hope this helps, and please keep asking questions. If need help with it, chances are someone else does too, and some of us feel good when asked a question that we can actually help with.

edit:  someone else will have to explain umask.  I don't know what that does.

---

### Post by JenniferDry on 2005-03-30
[QUOTE=digby]The way the mount command works isn't to complicated once you've used it a couple of times. After you get that first successful mount, you'll be fine. You said that you tried to mount your linux partition, but unless you have multiple distros, Ubuntu should mount all of it's partitions (/, /home, and swap on my machine) at boot time.
edit:  someone else will have to explain umask.  I don't know what that does.[/QUOTE]

I also have mepis installed and that is where all my files were.

Is umask the problem. It is the only thing I can think of

---

### Post by digby on 2005-03-30
I just went back and re-read your last comment.  I missed before that you had 
 

 /dev/hda7       /media/mepis    ext3    umask=000       0       0

When naming a specific filesystem, you have to put -t before it.  Try what you did before with

/dev/hda7 /media/mepis -t ext3

You can try it with and without umask.  I know that umask isn't necessary to mount something.  If that doesn't work, just try -t auto.

---

### Post by JenniferDry on 2005-03-30
First off: thank you both for all your help.
I tried both and got an unkown file type "t" during boot during the mount process.
Still no access.

---

### Post by odrop on 2005-03-30
Try something exactly like this:

sudo mount /dev/hda5 /media/mepis -t auto

You might need some extra options also (for permissions and stuff) that you can find in the man pages for mount.

---

### Post by Buffalo Soldier on 2005-03-30
I think here is your problem. Earlier you entered the command:```
david@ubuntu:~/Desktop$ sudo mkdir **/media/windows**

```Which means the directory you created is **/media/windows**. BUT your entry is fstab is```
/dev/hda7 **/media/mepis** ext3 umask=000 0 0
```What it means is you're trying to mount to a directory that does not exist. What your fstab entry should be is```
/dev/hda7 **/media/windows** ext3 umask=000 0 0
```

---

### Post by KongeOdin on 2005-04-01
I made the leap from windows yesterday, so I am quite new to this linux thing.
Used yesterday to install nvidia7167 drivers just to see that they had been added today.... :-& At least I learned something in the process. And the screensavers still doesnt work 
The next step is accessing my fat32 hard drives. Seems I can only keep one station mounted and accesible at a time.
Thanks for the much needed info. :smile:  
I have two questions:
1. Is there any way to automount, so I can play my favorite mp3s without having    to mount that drive everytime? 
2. How do I keep several stations mounted at a time( for instance hda1 and hda2 when working on two documents stationed on each drive)
3. If there is a way to automount and keep several stations mounted at a time, how do I automount all my stations on startup of Kubuntu (kde3.4)?

---

### Post by Buffalo Soldier on 2005-04-01
I don't know what you mean by *station*. But for your automount question as well as other Ubuntu frequently asked questions, you can find the answer at the well documented [UbuntuGuide.org](http://ubuntuguide.org/). The direct link to answer your specific question is [UbuntuGuide.org/#automountfat](http://ubuntuguide.org/#automountfat).

---

### Post by Beardy on 2005-04-01
Very easy to slag off a newbie for not being able to mount a partition but with a modern distro it shouldn't need to be done anyway. Automount is essential if we want others to accept Linux as a true alternative. I'm appalled at at the second post on here and as a many cups of something person should know better. Much easier to help than to  just criticise and point to an url.

Woof, woof.

---

### Post by Buffalo Soldier on 2005-04-01
Maybe you haven't had the pleasure of answering the same questions for the hundred time. But then again maybe you have, and I applaud your patience.

---

### Post by KongeOdin on 2005-04-01
well you see I ve allready tried the commands in this guide. 

Kubuntu doesnt understand the command "gedit" which is used in this guide for the auto mount of the stations. I think this is not for the version I am using, I think I am using the hoary (Using the 5.04 guide) while the 4.10 guide is for  another distribution or something

xxxxx@xxxxx:~$ sudo cp /etc/fstab /etc/fstab_backup
xxxxx@xxxxx:~$ sudo gedit /etc/fstab
sudo: gedit: command not found

Is there any way to make this command work or do I use a different command? 

By stations I mean the different partitions on my hardisk

---

### Post by Beardy on 2005-04-01
If from the same person a hundred times then maybe I would loose patience but we all have to start somewhere.  I can't get my wifi dongle to work, any takers.

""Ubuntu" is an ancient African word, meaning "humanity to others". Ubuntu also means "I am what I am because of who we all are". The Ubuntu Linux distribution brings the spirit of Ubuntu to the software world."


Woof, woof.

---

### Post by Beardy on 2005-04-01
nano, nano


Woof, woof

---

### Post by bored2k on 2005-04-01
[QUOTE=Beardy]If from the same person a hundred times then maybe I would loose patience but we all have to start somewhere.  I can't get my wifi dongle to work, any takers.

""Ubuntu" is an ancient African word, meaning "humanity to others". Ubuntu also means "I am what I am because of who we all are". The Ubuntu Linux distribution brings the spirit of Ubuntu to the software world."


Woof, woof.[/QUOTE]
 Stay on topic. Wifi problems go to networking section. 
And what is it with you and barks.

---

### Post by Buffalo Soldier on 2005-04-01
Replace the word **gedit** with whatever name your text editor in KDE.

---

### Post by KongeOdin on 2005-04-01
I found it out myself.
Had to start kdesu kate and find /etc then the file fstab and edit it according to the guide.

Hope I can keep several hardisk partitions mounted this way.   8-[ 
edit: Thanks for the help.

---

### Post by Beardy on 2005-04-01
My point is we all need a little help sometimes.

Use nano instead of gedit. Why that's bundled with it lord only knows.

Woof, woof.

---

### Post by KongeOdin on 2005-04-01
Seems like I still need help. Only one partition can be mounted in this way. 
Only the last station being mounted is accessible.
Is it possible to keep all mounted on the same time?
How do I do it?
 :confused:

---

### Post by digby on 2005-04-01
I'm not sure what you mean by station either... but I can't think of any reason that mounting one partition would unmount another... Are you trying to mount them to the same place perhaps?

---

### Post by Buffalo Soldier on 2005-04-01
[QUOTE=KongeOdin]Seems like I still need help. Only one partition can be mounted in this way. 
Only the last station being mounted is accessible.
Is it possible to keep all mounted on the same time?
How do I do it?
 :confused:[/QUOTE]
 What's the content of your */etc/fstab* file and the output of **sudo fdisk -l** command?

---

### Post by KongeOdin on 2005-04-02
Of course stupid me trying to mount all the drives to the same folder. That must be it. Sorry to being bothering you. Now I will try to mount the disks to different folders.

like /media/disk1 /media/disk2 etc.

This part of my fstab looked like this:
/dev/hda5       /media/windows    vfat    umask=000       0       0
/dev/hda1       /media/windows    vfat    umask=000       0       0

Now I will try this instead:
/dev/hda5       /media/windows1    vfat    umask=000       0       0
/dev/hda1       /media/windows2    vfat    umask=000       0       0

etc.

Thanks for the help
 :-)

---

### Post by KongeOdin on 2005-04-02
Hi. Seems like installing the hardisk partitions to different directories did the trick.
Now my fstab looks (almost) like the following and its working good. And i can play my mp3s while working.  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               reiserfs notail          0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda5       /media/windows1   vfat    umask=000       0       0
/dev/hda1       /media/windows2  vfat    umask=000       0       0
/dev/hda3       /media/windows3    vfat    umask=000       0       0
/dev/hda6       /media/windows4    vfat    umask=000       0       0
/dev/hdb5       /media/windows5    vfat    umask=000       0       0
/dev/hdb6       /media/windows6    vfat    umask=000       0       0

---

### Post by Rockrol913 on 2005-04-03
This is what you should do ...
You should install kynaptic the Package Manager.
Look for and install "pmount". 
It's under the utilities menu in kynaptic.
After it's installed just "mount" any of your drives and it will automaticly mount.
You will see the little green arrow to the bottom right od your drive. That means that it's mounted :)

---

### Post by Rockrol913 on 2005-04-03
I'm sorry...
Kynaptic is already installed. Go to it and look for pmount under utilities and install it.
You can mount from then on with no problems...

---

### Post by kristi on 2005-04-04
[QUOTE=Beardy]Very easy to slag off a newbie for not being able to mount a partition but with a modern distro it shouldn't need to be done anyway. Automount is essential if we want others to accept Linux as a true alternative. I'm appalled at at the second post on here and as a many cups of something person should know better. Much easier to help than to  just criticise and point to an url.

Woof, woof.[/QUOTE]

I agree - this is rediculous - I have about 8 partitions that I want mounted.  MDK and Xandros do it just fine.  Is there no utility that aids in the mounting of partitions?

There's this beautiful big icon called SYSTEM on the taskbar.  Storage media shows me all of my unmounted partitions.  But as far as I can see, no easy way to mount them - likt MDK's MCC.

And from the explainations I see, even the experts here do not know an easy way, or even how to mount them.
PLEASE!
Kristi

---

### Post by Buffalo Soldier on 2005-04-04
[QUOTE=kristi]There's this beautiful big icon called SYSTEM on the taskbar.  Storage media shows me all of my unmounted partitions.  But as far as I can see, no easy way to mount them - likt MDK's MCC.[/QUOTE]I hate to sound mean, but I have to ask... if MDK MCC is your prefered way of doing things... what brings you here?

There's a lot of *"easier"* ways, but writing your */etc/fstab* file couldn't be that hard for you? Or could it? Example:

output of **sudo fdisk -l** command:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19773     9965560+   c  W95 FAT32 (LBA)
/dev/hda2           19779       27525     3903795   83  Linux
/dev/hda3           27525       38537     5550457+  83  Linux
/dev/hda4           38537       39541      506047+  82  Linux swap / Solaris

```

Content of */etc/fstab* file```
# <file system> <mount point>   <type> 		<options>       <dump>	<pass>
/dev/hda1       /media/windows  vfat    	user,umask=000	0      	0
/dev/hda2       /               reiserfs 	notail         	0     	1
/dev/hda3       /home           reiserfs 	defaults       	0     	2
```

---

### Post by KongeOdin on 2005-04-04
For the kubuntu hoary package and (at least) fat32 (vfat) partitions.
First you have to make directories to mount each partition in. 
You do that in a terminal window.
K Menu --> Run command ( Also you may press the tabs options --> run in terminal window.).

Write the command like this:

sudo mkdir /media/harddisk1
Now you probably have to enter your password.
(To get up more terminal sessions in which you can enter commands, press the button on the bottom left)

Here you have made a folder named "harddisk1" to mount a partition in, located inside the "/media/" folder. 
You can choose any name you want for it. I dont know if this new folder has to be contained in the "/media/" folder, but at least it works this way.
You have to make one folder for each partition you want mounted.
For instance:

sudo mkdir /media/harddisk1
sudo mkdir /media/harddisk2
sudo mkdir /media/harddisk3

and so on...

After that you have to edit a file mounting the drives as the machine starts up.
This file is located in the folder "/etc/" and the file is named fstab.
The editor you can use for it is kate, which you bring up with the following command in the terminal window to get you all write permissions:

kdesu kate

The kate editor will show up (after you having entered your password again).
Inside the Kate editor you have to press:

file-->open 
then enter the location of the fstab file which is: /etc/ 
and open the location. Here you can find the fstab file and choose it.
At the end of this file enter:

/dev/hda5       /media/harddisk1    vfat    umask=000       0       0
/dev/hda1       /media/harddisk2    vfat    umask=000       0       0
/dev/hda3       /media/harddisk3    vfat    umask=000       0       0

NB! (The names of the hardisk partitions, like hda5, hda1 and hda3, will vary according to what drives you want mounted, change them accordingly)

Save the file and/or close the editor. restart the system (or xeditor).
Now I believe the selected disks will mount themselves. 

 :-)

---

### Post by kristi on 2005-04-04
"I hate to sound mean, but I have to ask... if MDK MCC is your prefered way of doing things... what brings you here?"

Perhaps you wear blinders.  I don't.

After six hundred some-odd posts, THIS is all you've learned??? :


[QUOTE=Buffalo Soldier]
output of **sudo fdisk -l** command:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19773     9965560+   c  W95 FAT32 (LBA)
/dev/hda2           19779       27525     3903795   83  Linux
/dev/hda3           27525       38537     5550457+  83  Linux
/dev/hda4           38537       39541      506047+  82  Linux swap / Solaris

```content of */etc/fstab* file```
# <file system> <mount point>   <type> 		<options>       <dump>	<pass>
/dev/hda1       /media/windows  vfat    	user,umask=000	0      	0
/dev/hda2       /               reiserfs 	notail         	0     	1
/dev/hda3       /home           reiserfs 	defaults       	0     	2
```[/QUOTE]

(I'm sure you could still find a C64 somewhere and do some REAL programming!!!)

mmmmm - got lots of numbers!!!   must be good!!!
Kristi

---

### Post by Buffalo Soldier on 2005-04-05
[QUOTE=kristi]"I hate to sound mean, but I have to ask... if MDK MCC is your prefered way of doing things... what brings you here?"

Perhaps you wear blinders.  I don't.

After six hundred some-odd posts, THIS is all you've learned??? :




(I'm sure you could still find a C64 somewhere and do some REAL programming!!!)

mmmmm - got lots of numbers!!!   must be good!!!
Kristi[/QUOTE]
 It gets my work done :) no complaints about Ubuntu.

---

### Post by emmbec on 2005-04-21
Hi, I tryed mounting my NTFS parititon but I get the following error:

[HTML][FONT=Courier New]root@theos:/boot/grub # mount /dev/hda1 /media/windows/ -t ntfs -o unmask=0222
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/FONT]
[/HTML]

the output of the sfdisk -l is this:

[HTML]root@theos:/boot/grub # sfdisk -l

Disk /dev/hda: 155061 cylinders, 16 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 516096 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/hda1   *      0+  77504   77505-  39062488+   7  HPFS/NTFS
/dev/hda2      77520  152808-  75289-  37945530   83  Linux
                start: (c,h,s) expected (1023,15,63) found (1023,254,63)
                end: (c,h,s) expected (1023,15,63) found (1023,254,63)
/dev/hda3     152808+ 155055-   2248-   1132582+   5  Extended
                start: (c,h,s) expected (1023,15,63) found (1023,254,63)
                end: (c,h,s) expected (1023,15,63) found (1023,254,63)
/dev/hda4          0       -       0          0    0  Empty
/dev/hda5     152808+ 155055-   2248-   1132551   82  Linux swap / Solaris
                start: (c,h,s) expected (1023,15,63) found (1023,254,63)
                end: (c,h,s) expected (1023,15,63) found (1023,254,63)
[/HTML]

I formated my HD the following way:

1 partition for windows NTFS as primary
1 partition for linux ext3 as parimary
1 swap for linux logical.

Hope you can solve my problem

---

### Post by KongeOdin on 2005-04-27
For me it looks lie it  is some kind of problem with the aprtition table. When I use windows I may use pqmagic for this management, and make a startup boot disk with the program on, then I can usually solve my rpoblems. Like repairing the table, formatting disks (lots of different formats for linux or windows) or moving data e.t.c. 
I am not shure what is the linux equivalent of this program.
To me it loooks like you have to fix your partitions or look at them with this kind of program before trying to mount them.

---

### Post by richpull on 2005-07-22
Can anyone please tell me how do i mount this

/dev/sda2           12880       25945   104952645    f  W95 Ext'd (LBA)

Thanks
Richard

---

### Post by bored2k on 2005-07-22
[QUOTE=richpull]Can anyone please tell me how do i mount this

/dev/sda2           12880       25945   104952645    f  W95 Ext'd (LBA)

Thanks
Richard[/QUOTE]
 You could try
1. sudo mkdir /media/windows
2. sudo gedit /etc/fstab 
Here you would add:
/dev/sda2       /media/windows  vfat    iocharset=utf8,umask=000   0       0
3. sudo mount -a

If that doesn't mount it, replace step 2 with
/dev/sda2       /media/windows  ntfs    nls=utf8,umask=0222 0       0

The mounted partition should be found in /media/windows

---

### Post by richpull on 2005-07-22
Unfortuantly it did not work

mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

This is an extended partition that i am trying to mount. The main partition is ntfs.

---

