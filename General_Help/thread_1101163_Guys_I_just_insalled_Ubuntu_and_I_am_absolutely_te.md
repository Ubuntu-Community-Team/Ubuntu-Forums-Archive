---
title: "Guys I just insalled Ubuntu and I am absolutely terrified"
date: 2009-03-20
forum: General Help
---

### Post by bruceleeroy on 2009-03-20
Hey everyone,
I just recently switch to Ubuntu from a windows machine that for obvious reasons I had enough of thinking that linux was the promise land. I was told there would be a learning curve but I had no idea it would be this steep. I was wondering if I could get some help.

I have two hard drives. The one I installed Ubuntu on has been given the name 'File System'.
I formated my second hard drive and partioned it as a ext2 and has been given the name '313.9 GB Media'

Now everything seemed fine but I cant do anything with either hard drive. They wont let me add folders or move things around at all. I assume it has something to do with the permissions but I can't for the life of me figure it out.

The second problem is everytime I click on the second HD '313.9 GB Media'
it says **System policy prevents mounting internal media** and then asks for my password. Do I honestly have to do this everytime I want to use it? Cant I just make it mount itself automatically when it boots up?

Lastly is their a way I can rename the Hard Drives?

Sorry for all the questions I am really at my wits end.

---

### Post by bodhi.zazen on 2009-03-20
First, welcome to Ubuntu.

Second, yes it does get easier.

Permissions are the hardest thing at first :

[FilePermissions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FilePermissions") 

I also advise you consider re-formating the partition to ext3. Not critical, but a journalled file system is probably better for preventing data loss.

To set your permissions, use chown and chmod.

To change the mount point, first unmount the drive and then edit fstab.

Then make a new directory as  your mount point and mount away.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

Do not let the size of those links overwhelm you, take your time and read them and soon (I hope) things well start to make sense,

---

### Post by mb_webguy on 2009-03-20
I'll answer this one guys.  It's just taking me a while to type it up.

EDIT:  CRAP!  Ninja'd by Bodhi!

---

### Post by pbpersson on 2009-03-20
When I wanted to add a second hard drive to my system and have it mount automatically, I used the instructions here:

[http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")

---

### Post by Simpotico on 2009-03-20
Congratulations, I'll drink to that!

---

### Post by sahabcse on 2009-03-20
Hi

Mounting NTFS partition permanently please follow below url


[http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html](http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html)

---

### Post by mb_webguy on 2009-03-20
First, in the words of St. John the Martyr -- and I'm referring to Dillinger, of course -- "Lie down on the floor and keep calm".

Now that you're nice and relaxed, I can explain your problems, why you have them, and what you need to do to fix them.

Linux isn't Windows.  While it can do just about everything Windows can do (and some it can't), it does them differently.  One big difference is the filesystem.

In Windows, partitions are assigned different drive letters, and so there are different filesystems under different "drives".  In Linux, however, there is only one filesystem, and partitions are mounted as directories.  Your second partition isn't being mounted because you haven't told the system to do it.  You could have done this easily during installation... if you'd known about it.  Don't worry, though.  You're a first-day newbie that stumbled on a third-day obstacle.

Partitions can be mounted anywhere in the filesystem, and any directory can be put on a separate partition.  So you could have mounted this second drive as "/home" (where all user data is stored) or "/usr" (where all user applications are stored) or even "/ipoopedmypants" (which doesn't exist, but is still perfectly all right if that's where you want to mount it).  

Generally, partitions that aren't mounted as a directory that has a predetermined purpose are mounted under the "/mnt" directory.  (Removable media is likewise mounted under the "/media" directory.)  

Now, I could tell you what to do to mount this second drive right now, but you'd just get frustrated because you don't yet know what the commands do.  Instead, I'm going to suggest you follow the links in Bodhi's post (which I was going to put in this post until he beat me to it).  Once you understand a bit of what's going on, you'll be able to mount that partition temporarily using three commands in the terminal, or permanently by editing one line in a text file.  

And I also second Bodhi's suggestion that you reformat that drive as ext3.  The difference between ext2 and ext3 is a bit like the difference between FAT32 and NTFS -- the latter is much improved over the former.

---

### Post by cfree220 on 2009-03-20
Thanks for posting this, bruceleeroy, I learned some new things about mount points that had not been clear to me before. Good luck as you venture into Ubuntu. I'm still pretty new to it to, but give it a week or two and you should start feeling a bit more comfortable.

---

### Post by bruceleeroy on 2009-03-20
You guys are awesome. These look like some great write-ups Ill start reading these immediately. Hopefully I dont brick my system :D

---

### Post by simtaalo on 2009-03-20
you'll be fine. those little things that might seem excessive and annoying now you will grow to understand are part of the inherent security of the system. read as much as you can and it will all slowly start to make sense.

you are where i was about a year ago, its definitely worth it :) i've learnt so much since then, and still have so much to learn.

btw is your userName influenced by the film character? i remember the film from years ago but don't remember the name of it.

---

### Post by fieroboom on 2009-03-20
> **sahabcse said:**
> Hi

Mounting NTFS partition permanently please follow below url


[http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html](http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html)

Why was this comment added? Nowhere does the OP mention NTFS...
We don't need to be confusing those new to linux that are already confused. :)

bruceleeroy, while I agree with the other posts that those are good writeups to read, I also understand how frustrating it can be to have a broken system and be forced to read a whole bunch of stuff for hours without a fix in site, so let's see if I can help you a little with your immediate issue... Please open a terminal (Applications -> Accessories -> Terminal), run this command and copy/paste the output here.
```
cat /etc/fstab
```
The purpose of that command will tell us what drives are getting mounted at bootup, and all of the options for them.
:D
-Paul

---

### Post by pbpersson on 2009-03-20
> **fieroboom said:**
> 
I agree with the other posts that those are good writeups to read, I also understand how frustrating it can be to have a broken system and be forced to read a whole bunch of stuff for hours without a fix in site

Yes....I looked at those pages and with all the things I have going on in my life, if I wanted to get my machine up and running and was told to read an encyclopedia of information just to mount a drive it would turn me off to Linux in an instant....just my opinion....apologies to those people who think you need to be a car mechanic in order to drive a car....  ;)

In all of those pages.....in all of those links to all other pages....there is a comment on one page that says, "or you could install this little GUI, click a couple of times, and ignore all these other instructions that would take you days to read" so I am wondering why that little GUI utility is not more widely publicized?

I have installed it and will be trying it this evening.  It has some funny name that meant nothing to me, like psmyd or something....I am adding two more drives to this machine that I am pulling from a test machine.

---

### Post by boof1988 on 2009-03-20
> **pbpersson said:**
> In all of those pages.....in all of those links to all other pages....there is a comment on one page that says, "or you could install this little GUI, click a couple of times, and ignore all these other instructions that would take you days to read" so I am wondering why that little GUI utility is not more widely publicized?

I have installed it and will be trying it this evening.  It has some funny name that meant nothing to me, like psmyd or something....I am adding two more drives to this machine that I am pulling from a test machine.

Is [*pysdm*](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=pysdm) the package you speak of (for use as a graphical storage device manager)?

---

### Post by pbpersson on 2009-03-20
> **boof1988 said:**
> Is [*pysdm*](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=pysdm) the package you speak of (for use as a graphical storage device manager)?

Yes, that is it!  I can't believe I remembered all the letters.  :D

Is that utility any good?  Has anyone tried it?

---

### Post by bruceleeroy on 2009-03-20
> **fieroboom said:**
> Why was this comment added? Nowhere does the OP mention NTFS...
We don't need to be confusing those new to linux that are already confused. :)

bruceleeroy, while I agree with the other posts that those are good writeups to read, I also understand how frustrating it can be to have a broken system and be forced to read a whole bunch of stuff for hours without a fix in site, so let's see if I can help you a little with your immediate issue... Please open a terminal (Applications -> Accessories -> Terminal), run this command and copy/paste the output here.
```
cat /etc/fstab
```
The purpose of that command will tell us what drives are getting mounted at bootup, and all of the options for them.
:D
-Paul

I think you guys might be the nicest people I have run into on a forum in a long time. I cant tell you how much I appreciate the assistance.

I typed in what you said and this is what came up.

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d8c35597-4eb6-4501-af0f-074751d6e857 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=533a7382-9d23-4a16-932d-49ab9dfac96c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
chris@otacon:~$

---

### Post by pbpersson on 2009-03-20
Staying within the realm of the command line world, the next step would be to type the following and post the output of this command:

```
sudo fdisk -l
```

That is a lowercase "L" at the end

---

### Post by bruceleeroy on 2009-03-20
Okay I just typed it in and this is what came up.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ac9fe19

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac3fac3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38157   306496071   83  Linux
/dev/sdb2           38158       38913     6072570    5  Extended
/dev/sdb5           38158       38913     6072538+  82  Linux swap / Solaris

---

### Post by bruceleeroy on 2009-03-20
This is another thing I dont understand.

Device Boot Start End Blocks Id System
/dev/sdb1 1 38157 306496071 83 Linux
/dev/sdb2 38158 38913 6072570 5 Extended
/dev/sdb5 38158 38913 6072538+ 82 Linux swap / Solaris 

Is the sbd1,2,5 the names the hard drives have been given?

---

### Post by pbpersson on 2009-03-20
> **bruceleeroy said:**
> Okay I just typed it in and this is what came up.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ac9fe19

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac3fac3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38157   306496071   83  Linux
/dev/sdb2           38158       38913     6072570    5  Extended
/dev/sdb5           38158       38913     6072538+  82  Linux swap / Solaris

The first hard drive on your system is sda and it is 80GB in size.

The second hard drive on your system is sdb and it is 320GB in size

sdb1, sdb2, and sdb5 are partitions on your second hard drive

---

### Post by fieroboom on 2009-03-20
> **bruceleeroy said:**
> Okay I just typed it in and this is what came up.

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac3fac3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38157   306496071   83  Linux
/dev/sdb2           38158       38913     6072570    5  Extended
/dev/sdb5           38158       38913     6072538+  82  Linux swap / Solaris

The above section indicates that your OS sees the drive and it's partitions, but...

> **bruceleeroy said:**
> 
I typed in what you said and this is what came up.

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d8c35597-4eb6-4501-af0f-074751d6e857 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=533a7382-9d23-4a16-932d-49ab9dfac96c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
chris@otacon:~$

The above indicates that it's not being mounted at boot time.
Questions:
- Why do you have it formatted as if you're installing linux on it? If it's just a backup/secondary drive, then it only needs one partition... At least until you get a little more advanced. ;)
- Where do you want it mounted? For example, I mount my second drive to /save.

Answering those questions will determine the next course of action.


> **bruceleeroy said:**
> This is another thing I dont understand.

Device Boot Start End Blocks Id System
/dev/sdb1 1 38157 306496071 83 Linux
/dev/sdb2 38158 38913 6072570 5 Extended
/dev/sdb5 38158 38913 6072538+ 82 Linux swap / Solaris 

Is the sbd1,2,5 the names the hard drives have been given?

No, those are the device nodes... basically just the simple location of where they are attached. The letters sdb indicate that it is referred to as 'SCSI Disk B', and the numbers are the partitions.
:D
-Paul

---

### Post by psychomichael on 2009-03-20
I'm having a similar problem except it's not a hard drive I'm trying to mount, it's a second cdrom. I already created a directory in my media folder called cdrom2 but am not sure where to go from there...

---

### Post by bruceleeroy on 2009-03-20
> **fieroboom said:**
> 
The above indicates that it's not being mounted at boot time.
Questions:
- Why do you have it formatted as if you're installing linux on it? If it's just a backup/secondary drive, then it only needs one partition... At least until you get a little more advanced. ;)
- Where do you want it mounted? For example, I mount my second drive to /save.

Answering those questions will determine the next course of action.

-Paul

Hey Paul,
Sorry for my sporadic responses work is being a pain today. Anyway I installed Linux on the 80 GB hard drive. The Second HD that is 320 GB is purely a extra storage drive I had absolutely no idea what I was doing when I formated it I just found Gparted and used that. If I should do it in a more efficient manner I will follow whatever direction you think I should go.

Unfortunately I don't know exactly what you mean when you say where I want it mounted. Since my knowledge of file structures is simply windows based(The almighty C:/ being as far as it goes) I didn't know you needed to mount a hard drive in a specific location.

---

### Post by 1ronlung on 2009-03-20
I understand your point.  Linux is scary.  I've got a degree in software development, so it's not like I'm not computer literate.
It seems like every single thing I want to do would take 2 secs in W2K, but has a legion of complications in Ubuntu - and that's the user friendly Linux !
Didn't help that I got caught with a Broadcom chipped Wifi card when I first installed.  Took me about 2 weeks to sort that one out ;)
Good news is that all the info I've needed so far has been out on the net and easy to find.  It's constant work, but I'm quite enjoying it.. Reminds me of my 8bit/16bit days when everything was an adventure.
Hey, it keeps me off the streets :P

Good Luck, 
ironlung

---

### Post by fieroboom on 2009-03-20
> **bruceleeroy said:**
> Hey Paul,
Sorry for my sporadic responses work is being a pain today. Anyway I installed Linux on the 80 GB hard drive. The Second HD that is 320 GB is purely a extra storage drive I had absolutely no idea what Iwas doing when I formated it I just found Gparted and used that. If I should do it in a more efficient manner I will follow whatever direction you think I should go.

Unfortunately I don't know exactly what you mean when you say where I want it mounted. Since my knowledge of file structures is simply windows based(The almighty C:/ being as far as it goes) I didn't know you needed to mount a hard drive in a specific location.

Ok, crash course comparison... ;)
Windows Root Dir - C:\
Linux Root Dir - /

Windows User Home Dir - C:\Documents And Settings\Username
Linux User Home Dir - /home/username

So me mounting my second drive on /save would be similar to taking D:\ and mapping it to C:\save in Windows...
...but yet it's so much different since Windows assigns a new drive letter to a new drive.
Anyway, for now, I'm just going to tell you what to do, and you can feel free to change it whenever you feel more comfortable in the Linux world... :) That sound ok?

First, you need to open up gparted again (if that's your preferred tool), and erase all the partitions. Then, create a single new partition formatted as ext3 (it might just be called 'linux' in gparted,not sure...). Apply the changes, then close gparted.
Then, open a terminal, and run these commands:
```
sudo mkdir /media/save
```
This will create a folder in /media/ which we'll use for a mountpoint.
```
sudo chown USERNAME\: !$
```
Replace USERNAME with your username. This will change ownership of said folder to you.
* As a side note, the \: after USERNAME is shorthand for USERNAME:USERNAME, and !$ (pronounced as "bang dollar") is a variable that stores that last command line argument you used. In other words, you can also run that same command this way:
```
sudo chown USERNAME:USERNAME /media/save
```
Moving on:
```
sudo chmod 777 !$
```
This will change the permissions on said mountpoint to world readable, writable, & executable. Mounted drives will inherit the permissions of their mountpoints, so this is what I usually do.

Now you have your drive partitioned, and your mountpoint made, so all we need to do is tell the OS where to mount it.
First:
```
sudo cp /etc/fstab /etc/fstab_bak
```
This will make a copy of your current working fstab in case anything goes wrong, and your main drive won't boot.
Then:
```
gksudo gedit /etc/fstab
```
This will open fstab in gedit so you can add your newly partitioned drive.
Right after this line:
```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```
You need to enter this:
```
/dev/sdb1/	/media/save	auto	auto,defaults,errors=remount-ro	0	1
```
This will tell Ubuntu to mount that new single partition on /dev/sdb to the mountpoint you created, /media/save, it will auto-determine the filesystem type, and do a few other things... If you want more info on that, see [this page.](http://www.tuxfiles.org/linuxhelp/fstab.html)

Once you have added that line, save the file, and close gedit. Now you can finally mount that drive by opening a terminal (Applications->Accessories->Terminal), and issuing this command:
```
sudo mount -a
```
That tells Ubuntu to mount everything described in /etc/fstab.

Then come back and tell us how it went...
:D
-Paul

EDIT:
Whew, sorry for the novel... I get excited helping sometimes. ;)

---

### Post by pbpersson on 2009-03-20
> **fieroboom said:**
> 
Then come back and tell us how it went...
:D
-Paul


Hey.....question from the audience....what is the advantage of doing this in /media/save instead of /MySecondHardDrive or /home/phil/MySecondHardDrive?

I am just wondering because I will be adding more hard drives to this machine later tonight.


Phil

---

### Post by fieroboom on 2009-03-20
> **pbpersson said:**
> Hey.....question from the audience....what is the advantage of doing this in /media/save instead of /MySecondHardDrive or /home/phil/MySecondHardDrive?

I am just wondering because I will be adding more hard drives to this machine later tonight.


Phil

There isn't an advantage. You technically can mount the drive anywhere you want. It's just better to keep it away from the root directory (/), because that further decreases you risk of a big "OOPS". Also, /media is Ubuntu's default place for extra media to get mounted, such as CDs, flash drives, etc, so it's a good place for it.
:D
-Paul

---

### Post by bruceleeroy on 2009-03-20
Paul..
You are my hero bro that write up is incredible and I can actually understand it!

This is my first dumb question. When you say erase all the partitions do you mean of just the STORAGE drive or both Drives even the one that has Linux on it?

---

### Post by fieroboom on 2009-03-20
> **bruceleeroy said:**
> Paul..
You are my hero bro that write up is incredible and I can actually understand it!

This is my first dumb question. When you say erase all the partitions do you mean of just the STORAGE drive or both Drives even the one that has Linux on it?

Oh, wow, I can't believe I missed that. ONLY the storage drive (/dev/sdb)! Man, I'm sorry, I definitely should have specified that... Good thing you can't run it on a mounted drive!
:D
-Paul

---

### Post by bruceleeroy on 2009-03-20
Ha! Your dealing with a invalid bro you got to specify these things to me or else Ill end up trying to install Mac OSX on top of this.
[I]
One more thing.[/I]
Gparted gives me the option to make it the primary partition or a extended partition. I am assuming I want it to be the Extended right? Since The primary is probably already on the hard drive that linux installed to.

Hmm..Must be Primary cause if I do Extended it doesn't let me choose what kind of Filesystem I want it to be.

---

### Post by bodhi.zazen on 2009-03-20
> **bruceleeroy said:**
> Ha! Your dealing with a invalid bro you got to specify these things to me or else Ill end up trying to install Mac OSX on top of this.

We are here to support you if you wish to learn to use Ubuntu. There is nothing wrong with OSX so if you prefer that ...

If you wish to stay with Ubuntu, as with any OS, there will be a learning curve.
[I]
> One more thing.[/I]
Gparted gives me the option to make it the primary partition or a extended partition. I am assuming I want it to be the Extended right? Since The primary is probably already on the hard drive that linux installed to.

Hmm..Must be Primary cause if I do Extended it doesn't let me choose what kind of Filesystem I want it to be.

See : [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018")

---

### Post by bruceleeroy on 2009-03-20
> **bodhi.zazen said:**
> We are here to support you if you wish to learn to use Ubuntu. There is nothing wrong with OSX so if you prefer that ...

If you wish to stay with Ubuntu, as with any OS, there will be a learning curve.
[I]


See : [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018")

Oh man I didn't mean I was going to switch to OSX only that I am so lost I might accidentally try and install it thinking its Linux unless given specific instruction not to...get it...ahh it was a bad joke.

Truthfully though the amount of help has been staggering from everyone I cant believe it and cant express how much I appreciate it. Any community that is this helpful is one I want to be a part of. :D

---

### Post by fieroboom on 2009-03-20
> **bruceleeroy said:**
> Ha! Your dealing with a invalid bro you got to specify these things to me or else Ill end up trying to install Mac OSX on top of this.
[I]
One more thing.[/I]
Gparted gives me the option to make it the primary partition or a extended partition. I am assuming I want it to be the Extended right? Since The primary is probably already on the hard drive that linux installed to.

Hmm..Must be Primary cause if I do Extended it doesn't let me choose what kind of Filesystem I want it to be.

;) It's primary. You're allowed 4 primary partitions, and you can do extended partitions & logical drives underneath those if you need further chopping. But for your purposes, just create one primary partition, linux (ext3) format.
If you want further reading on partitioning, have a look at [wikipedia's writeup](http://en.wikipedia.org/wiki/Partition_(computing))
In my defense, I think I assumed you knew what to do in gparted, since you had already partitioned it once. Moral: don't assume.
:D
-Paul

---

### Post by bruceleeroy on 2009-03-20
Awesome Paul.
Now I am continuing the journey.

Does it matter the label I give it?

---

### Post by fieroboom on 2009-03-20
> **bruceleeroy said:**
> Awesome Paul.
Now I am continuing the journey.

Does it matter the label I give it?

Nope. Label is so you can identify it.
:D
-Paul

---

### Post by bruceleeroy on 2009-03-20
Okay so I finished everything then restarted my computer.
I opened STORAGE in the browser window it asked me to put in my Username and Password to mount it. Once I did there is just a lost+found folder that I cant open cause it says I dont have permissions and I cant add folders still. Hopefully I didn't screw something up.

I also still cant add any folders in the Main Hard Drive 76.7 GB Media.

**This is the current fstab output:**

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d8c35597-4eb6-4501-af0f-074751d6e857 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=533a7382-9d23-4a16-932d-49ab9dfac96c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1/	/media/save	auto	auto,defaults,errors=remount-ro	0	1
chris@otacon:~$ 

**And the fdisk**

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac3fac3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ac9fe19

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris

---

### Post by fieroboom on 2009-03-20
> **bruceleeroy said:**
> Okay so I finished everything then restarted my computer.
I opened STORAGE in the browser window it asked me to put in my Username and Password to mount it. Once I did there is just a lost+found folder that I cant open cause it says I dont have permissions and I cant add folders still. Hopefully I didn't screw something up.

I also still cant add any folders in the Main Hard Drive 76.7 GB Media.

Ok, open a terminal: Applications->Accessories->Terminal
Input these commands, and copy/paste the output here.
```
cat /etc/fstab
```
You already know what this does... ;)
```
cat /etc/mtab
```
This shows what's currently mounted
```
sudo fdisk -l
```
You should also already know what this does... :)
```
ls -al /media
```
This will show all the items in /media, as well as their permissions.
:D
-Paul

---

### Post by bruceleeroy on 2009-03-20
```
cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d8c35597-4eb6-4501-af0f-074751d6e857 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=533a7382-9d23-4a16-932d-49ab9dfac96c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1/	/media/save	auto	auto,defaults,errors=remount-ro	0	
```
cat /etc/mtab
```
/dev/sdb1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-11-generic/volatile tmpfs rw,mode=755 0 0
/dev/sdb1 /media/save ext3 rw,errors=remount-ro 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/chris/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=chris 0 0
/dev/sda1 /media/Storage ext3 rw,nosuid,nodev,uhelper=hal 0 0

```
sudo fdisk -l
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac3fac3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ac9fe19

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris

```
ls -al /media
```
ls -al /media

---

### Post by bruceleeroy on 2009-03-20
Oops here is the ls -al /media

total 24
drwxr-xr-x  5 root root 4096 2009-03-20 19:58 .
drwxr-xr-x 19 root root 4096 2009-03-18 22:35 ..
lrwxrwxrwx  1 root root    6 2009-03-17 17:54 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2009-03-17 17:54 cdrom0
-rw-r--r--  1 root root   62 2009-03-20 19:58 .hal-mtab
-rw-------  1 root root    0 2009-03-20 19:57 .hal-mtab-lock
drwxr-xr-x 19 root root 4096 2009-03-18 22:35 save
drwxr-xr-x  3 root root 4096 2009-03-20 19:14 Storage

---

### Post by fieroboom on 2009-03-20
Ok, we have a small issue... You have /dev/sdb1 mounted twice:

> **bruceleeroy said:**
> 	
```
cat /etc/mtab
```
**/dev/sdb1 / ext3 rw,relatime,errors=remount-ro 0 0**
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-11-generic/volatile tmpfs rw,mode=755 0 0
**/dev/sdb1 /media/save ext3 rw,errors=remount-ro 0 0**
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/chris/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=chris 0 0
/dev/sda1 /media/Storage ext3 rw,nosuid,nodev,uhelper=hal 0 0


And now that I look at it more closely, it's my mistake. Earlier I kept thinking that your second drive is /dev/sdb, and it's not. So you need to unmount /dev/sda1 and the duplicate of /dev/sdb1, correct the line in fstab, then we'll give it another go.
Unmount /dev/sda:
```
sudo umount /dev/sda1
```
Then unmount the duplicate /dev/sdb:
```
sudo umount /media/Storage
```
Now open fstab for editing:
```
gksudo gedit /etc/fstab
```
First, let's fix the comment that threw me off... Find these lines:
```
**# /dev/sda1**
UUID=d8c35597-4eb6-4501-af0f-074751d6e857 / ext3 relatime,errors=remount-ro 0 1
**# /dev/sda5**
UUID=533a7382-9d23-4a16-932d-49ab9dfac96c none swap sw 0 0
```
And change the **bold** lines to something like "80GB #1" and "80GB #5. It's just a comment, so anything will work, just make sure it's identifiable as the main 80G drive.
Now, we need to fix the last line you previously added (it's wrong because I told you the wrong thing to put). Since it's already using UUIDs everywhere else, let's go ahead and follow that trend so it looks nice.
First, run this command:
```
blkid /dev/sda1
```
In the output of that command, you'll see something like:
```
UUID="<REALLY-LONG-NUMBER-WITH-LETTERS>"
```
Highlight just the number that's between the quotes, right click, and copy. Now, back in gedit, find this line:
```
/dev/sdb1/ /media/save auto auto,defaults,errors=remount-ro 0
```
and change it to:
```
UUID=PASTE-THE-LONG-NUMBER-HERE /media/save auto auto,defaults,errors=remount-ro 0 1
```
* Side note - you can add your own comment above this line if you like. It needs to look something like this:
```
# 320GB STORAGE
```
Just make sure the line starts with a pound (#) to make it a comment that the OS ignores.
Then save the file, close gedit, and in the terminal, issue this command again:
```
sudo mount -a
```
And that should be it.
:D
-Paul

---

### Post by bruceleeroy on 2009-03-21
Paul,
Let me reiterate what a absolute savior you have been through this whole thing. Thanks so much for the help.

I ran through the process and this is what happened:
> **fieroboom said:**
> 
Unmount /dev/sda:
```
sudo umount /dev/sda1
```
Then unmount the duplicate /dev/sdb:
```
sudo umount /media/Storage
```

[INDENT][COLOR="Red"]I can only unmount 1 of these drives.[/COLOR] If I umount sda1 it tells me Storage is not mounted. If I umount storage first it then tells me:
[B]chris@otacon:~$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted[/B]

Despite this I continued to plow ahead since I figured they both must be unmounted. 
[/INDENT]


Now open fstab for editing:
```
gksudo gedit /etc/fstab
```
First, let's fix the comment that threw me off... Find these lines:
```
**# /dev/sda1**
UUID=d8c35597-4eb6-4501-af0f-074751d6e857 / ext3 relatime,errors=remount-ro 0 1
**# /dev/sda5**
UUID=533a7382-9d23-4a16-932d-49ab9dfac96c none swap sw 0 0
```
And change the **bold** lines to something like "80GB #1" and "80GB #5. It's just a comment, so anything will work, just make sure it's identifiable as the main 80G drive.
Now, we need to fix the last line you previously added (it's wrong because I told you the wrong thing to put). Since it's already using UUIDs everywhere else, let's go ahead and follow that trend so it looks nice.
First, run this command:
```
blkid /dev/sda1
```
In the output of that command, you'll see something like:
```
UUID="<REALLY-LONG-NUMBER-WITH-LETTERS>"
```
Highlight just the number that's between the quotes, right click, and copy. Now, back in gedit, find this line:
```
/dev/sdb1/ /media/save auto auto,defaults,errors=remount-ro 0
```
and change it to:
```
UUID=PASTE-THE-LONG-NUMBER-HERE /media/save auto auto,defaults,errors=remount-ro 0 1
```
* Side note - you can add your own comment above this line if you like. It needs to look something like this:
```
# 320GB STORAGE
```

[INDENT]**[COLOR="Red"]Okay I updated those so that my fstab looks like this:[/COLOR]**
# /80GB #1
UUID=d8c35597-4eb6-4501-af0f-074751d6e857 /               ext3    relatime,errors=remount-ro 0       1
# /80GB #5
UUID=533a7382-9d23-4a16-932d-49ab9dfac96c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# 320GB STORAGE
UUID=87e073f6-289c-47c5-a883-55e16885b01f/media/save	auto	auto,defaults,errors=remount-ro	0	1[/INDENT]

Just make sure the line starts with a pound (#) to make it a comment that the OS ignores.
Then save the file, close gedit, and in the terminal, issue this command again:
```
sudo mount -a
```
[INDENT]
Now this is where I think I must have done something wrong because when I type sudo mount -a it says:
**mount: mount point auto does not exist**[/INDENT]
[COLOR="Red"]
When I run my mtab this is what currently is displayed:[/COLOR]
```
**/dev/sdb1 / ext3 rw,relatime,errors=remount-ro 0 0**
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-11-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/chris/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=chris 0 0
```

Now it looks like its no longer duplicating so that has to be good right?



---

### Post by fieroboom on 2009-03-21
> **bruceleeroy said:**
> Paul,
Let me reiterate what a absolute savior you have been through this whole thing. Thanks so much for the help.

I ran through the process and this is what happened:

Yeah, I've been trying to edit my post since lastnight, but UbuntuForums kept giving me 503 errors and database errors...
The umount command that didn't work should have been /media/save/
```
sudo umount /media/save
```
I submitted the post, then immediately realized it was incorrect, but haven't been able to edit or post anything until now...

Also, your fstab is *almost* correct. You left out a space between the UUID number and the mountpoint. Here's what you have:
```
# 320GB STORAGE
UUID=87e073f6-289c-47c5-a883-55e16885b01f/media/save auto auto,defaults,errors=remount-ro 0 1
```
and here's what it should be:
```
# 320GB STORAGE
UUID=87e073f6-289c-47c5-a883-55e16885b01f /media/save auto auto,defaults,errors=remount-ro 0 1
```
Note the space between the 'f' of the UUID and /media/save. Correct that entry, and you should be golden. From your post, it looks like the duplication is gone, so no need to try the umount cmd again.
:D
-Paul

---

### Post by bruceleeroy on 2009-03-21
I know I couldn't reply till this morning.

Okay I updated the Fstab and I mounted it again with the sudo mount -a
which gave me no errors. 

However,
I still cant edit the drive or add folders :( Do I have to restart?

Im sorry man I am probably screwing something up.

---

### Post by heiNey on 2009-03-21
i think you can't make any folders or add any files because all the permissions belong to root.  you need to

```


sudo chown -R user:user /media/save


```

that code tells the system to make the folder /media/save belong to the user named 'user'.  you should put your own user name in there,   The -R means recursive, which means apply the same command to all files/folders in that folder

Do the same thing for your 'Storage' drive.

that's what i do, but im not sure about everyone else, since im a n00b too.

---

### Post by bruceleeroy on 2009-03-21
Okay something intresting happened when I changed the permission.

In the Storage drive their was a folder called **"lost+found"** that was locked but now I can open it. However I still cant add folders :(

What is the path name for my file system drive?
I know /media/save is for the Storage drive but what do I write to get permissions for the main 80GB drive?
```

# /80GB #1
UUID=d8c35597-4eb6-4501-af0f-074751d6e857 /               ext3    relatime,errors=remount-ro 0       1
# /80GB #5
UUID=533a7382-9d23-4a16-932d-49ab9dfac96c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# 320GB STORAGE
UUID=87e073f6-289c-47c5-a883-55e16885b01f /media/save	auto	auto,defaults,errors=remount-ro	0	1
```

Also I don't know if this would have any bearing on the permissions but in my explorer type window my name is 'chris' all lower case but next to the shut down button in the top right of Ubuntu its 'Chris'

---

### Post by heiNey on 2009-03-21
i dont see a /home drive.  did you not make one?

that lost+found folder is some default folder ubuntu makes.  im not really sure what its for either. heh.

your / should remain as root.

do this:

```


sudo chmod -R 755 /media/save


```

---

### Post by fieroboom on 2009-03-21
> **bruceleeroy said:**
> Okay something intresting happened when I changed the permission.

In the Storage drive their was a folder called **"lost+found"** that was locked but now I can open it. However I still cant add folders :(

What is the path name for my file system drive?
I know /media/save is for the Storage drive but what do I write to get permissions for the main 80GB drive?
```

# /80GB #1
UUID=d8c35597-4eb6-4501-af0f-074751d6e857 /               ext3    relatime,errors=remount-ro 0       1
# /80GB #5
UUID=533a7382-9d23-4a16-932d-49ab9dfac96c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# 320GB STORAGE
UUID=87e073f6-289c-47c5-a883-55e16885b01f /media/save	auto	auto,defaults,errors=remount-ro	0	1
```

Also I don't know if this would have any bearing on the permissions but in my explorer type window my name is 'chris' all lower case but next to the shut down button in the top right of Ubuntu its 'Chris'

Ok, now we need to take a step back and look at what you have. As mentioned before, /media/save should belong to your username, but instead of changing anything yet, let's have a look:
```
ls -al /media
```
And to be sure we know *exactly* what your username is (lower case vs capitalized), run this:
```
whoami
```
Post the results of those commands, and we'll go from there. If it's any consolation, you're very close!
:D
-Paul

---

### Post by heiNey on 2009-03-21
as for your question on how to get permissions for your 80 gig drive, you might want to open up gparted again (probably from the livecd, since you need to unmount the drive and resize it).  

you will need to resize the / partition to make it 5 to 10 gigs.  ubuntu only needs like 3, but i have it set to 10, in case i want to add a bunch of programs later.  then with the remaining space, you can make a new partition.  format that new partition, (should be roughly 65 gigs).  you should now have three partitions on the 80 gig drive (10 gig, 65 gigs, swap).

im not sure if gparted will let you, but if you can, make the mount point for the 65 gig to be /home/<username>.  reboot and you should have a /home/<username> drive.  do the chown and chmod stuff above for the /home/<username> folder and you should be able to write to that drive.

---

### Post by bruceleeroy on 2009-03-21
> **fieroboom said:**
> Ok, now we need to take a step back and look at what you have. As mentioned before, /media/save should belong to your username, but instead of changing anything yet, let's have a look:
```
ls -al /media
```
And to be sure we know *exactly* what your username is (lower case vs capitalized), run this:
```
whoami
```
Post the results of those commands, and we'll go from there. If it's any consolation, you're very close!
:D
-Paul

Alright this is what came up for:

**ls -al /media**

> total 16
drwxr-xr-x  4 root  root  4096 2009-03-21 08:53 .
drwxr-xr-x 19 root  root  4096 2009-03-18 22:35 ..
lrwxrwxrwx  1 root  root     6 2009-03-17 17:54 cdrom -> cdrom0
drwxr-xr-x  2 root  root  4096 2009-03-17 17:54 cdrom0
-rw-r--r--  1 root  root     0 2009-03-21 08:53 .hal-mtab
-rw-------  1 root  root     0 2009-03-21 08:26 .hal-mtab-lock
drwxr-xr-x  3 chris chris 4096 2009-03-20 19:14 save

**whoami**
```

chris@otacon:~$ whoami
chris
```

---

### Post by fieroboom on 2009-03-21
> **bruceleeroy said:**
> Alright this is what came up for:

**ls -al /media**



**whoami**
```

chris@otacon:~$ whoami
chris
```

That all looks good. If you're still having issues, try rebooting, since we accidentally double mounted the main drive, and did a lot. Assuming there are no errors, it should mount everything normally, and you should have permissions to write to them.
:D
-Paul

---

### Post by WatchingThePain on 2009-03-21
You can do it put your back into it-ice cube.

---

### Post by bruceleeroy on 2009-03-21
Paul it worked!
All I had to do was reboot it.

You are so awesome thanks man!

Is there a way I can change the permissions of the File System so that it lets me add folders there to?

---

### Post by boof1988 on 2009-03-21
> **bruceleeroy said:**
> Is there a way I can change the permissions of the File System so that it lets me add folders there to?

Can you post the output of the following?  It will show the current permissions for the directory of which you want to change permissions.

```
ls -al /path/to/directory/you/want/to/create/folder/in/
```

If we know the directory path, we can help you with the commands needed to change permissions.

---

### Post by fieroboom on 2009-03-21
> **bruceleeroy said:**
> Paul it worked!
All I had to do was reboot it.

You are so awesome thanks man!

Is there a way I can change the permissions of the File System so that it lets me add folders there to?

You should be able to... You own it, and you have read, write, & execute permissions... Give me the output from this one more time, since you've rebooted:
```
ls -al /media
```
:D
-Paul

---

### Post by bruceleeroy on 2009-03-21
Here is the output:
```

chris@otacon:~$ ls -al /media
total 16
drwxr-xr-x  4 root  root  4096 2009-03-21 14:11 .
drwxr-xr-x 19 root  root  4096 2009-03-18 22:35 ..
lrwxrwxrwx  1 root  root     6 2009-03-17 17:54 cdrom -> cdrom0
drwxr-xr-x  2 root  root  4096 2009-03-17 17:54 cdrom0
-rw-r--r--  1 root  root     0 2009-03-21 14:11 .hal-mtab
drwxr-xr-x  9 chris chris 4096 2009-03-21 13:57 save

```

---

### Post by fieroboom on 2009-03-21
> **bruceleeroy said:**
> Here is the output:
```

chris@otacon:~$ ls -al /media
total 16
drwxr-xr-x  4 root  root  4096 2009-03-21 14:11 .
drwxr-xr-x 19 root  root  4096 2009-03-18 22:35 ..
lrwxrwxrwx  1 root  root     6 2009-03-17 17:54 cdrom -> cdrom0
drwxr-xr-x  2 root  root  4096 2009-03-17 17:54 cdrom0
-rw-r--r--  1 root  root     0 2009-03-21 14:11 .hal-mtab
drwxr-xr-x  9 chris chris 4096 2009-03-21 13:57 save

```

Everything looks good... Are you sure you're attempting to write to the correct folder? Try this without sudo:
```
mkdir /media/save/test
```
It should just drop to the next line. If it does, then run this:
```
ls -al /media/save/
```
If the 'test' folder is listed, then run this:
```
nautilus /media/save &
```
Once Nautilus opens, you should see the test folder. Right click and try to create a new folder in nautilus. Then report back and let us know what happened.
:D
-Paul

---

### Post by bruceleeroy on 2009-03-22
Paul,
It all works perfect. My life is complete because of you.

---

### Post by fieroboom on 2009-03-22
> **bruceleeroy said:**
> Paul,
It all works perfect. My life is complete because of you.

One last note... On the 80GB drive, the only place you should be able to create folders/write without sudo is in your home directory (/home/chris/). Anywhere else will require super user powers.
Glad I could help!
:D
-Paul

---

