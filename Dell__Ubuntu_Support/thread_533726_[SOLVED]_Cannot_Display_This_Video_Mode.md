---
title: "[SOLVED] Cannot Display This Video Mode"
date: 2007-08-24
forum: Dell  Ubuntu Support
---

### Post by jaezcurra on 2007-08-24
Hi, I am quite a newbie to Linux
 In the recent days I was able to install Ubuntu twice in 2 different computers running Windows XP by the means of Wubi.  I had not big problems and I am able to play around and becoming used to wonderful Ubuntu (which I love a lot).
Now I am failing with a 3rd computer ( a Dell Dimension 8400 with an NVIDIA GeForce 6800 card and a Dell 1905FP [Analog] monitor).
Everything seems OK until the last and final reboot.  Just when there is going to be the switch to the GUI mode, I get a blank screen with the message: "1: Analog Input           Cannot Display This Video Mode".
I have tried with Ctrl-Alt-F1 to switch to text mode to be able to use commands to apply several advices to workaround this issue as I have seen surfing Ubuntu forums.
But I am requested to login and although I key my username and Password, I am not allowed to and I remain stuck.
Anyone could help?
TIA and best regards.

---

### Post by ridgeland on 2007-08-24
You see GRUB go by on the way to the dead screen.
Maybe you can change GRUB to boot as single user (root) and do the edits then
[http://ubuntuforums.org/showthread.php?t=528849](http://ubuntuforums.org/showthread.php?t=528849)
talks about changing GRUB during the boot to switch to single user mode.

NEW:
On booting the Ubuntu 7.10 LiveCD using a Dell monitor I click the first option on the menu "Start or Install" after a while I get to the "Cannnot Display This Video Mode".  Then [Alt]+[Ctrl]+[F1].  at the $ prompt: 
$ sudo su
# nano /etc/X11/xorg.conf
page down to Section "Monitor" change HorizSynch from 30-70 to 30-50, change VertRefresh from 50-160 to 50-100. [Ctrl]+O to "writeout" to same name then [Ctrl]+X to exit nano.  Now 
# ps -C Xorg
shows the process number to kill like 8441 USE YOUR NUMBER IN THE NEXT LINE
# kill 8441
Then it starts the GUI with a login (10 seconds and it goes away) then I'm at the GUI.

---

### Post by jaezcurra on 2007-08-25
Solved!

Finally, my real problem was to get to Recovery Mode, what I could achieve by pressing Esc nearly as ubuntu was beginning to launch.
After that, I entered "sudo dpkg-reconfigure xserver-xorg" and I chose "VESA" and everything is going seamlessly.
Best regards.

---

### Post by ridgeland on 2007-08-25
Great.
jaezcurra,
Don't forget to go to the top of this tread click on "Thread Tools" and select "Mark as Solved".  This helps both others seeking answers and those wanting to help.
Thanks.

---

### Post by boxfullofheads on 2008-03-23
Hi, 
I am Noob to Linux
I am getting this same thing Cannot Display This Video Mode
I have DELL XPS-4 with a NVIDIA GeForce 6800 video card
and a DELL E173FP flat LCD monitor...
Extream Noob this is the first time trying Linux
i always wanted to give it a try

---

### Post by ridgeland on 2008-03-23
Hi boxfullofheads,

Hope you find the forums useful, I have.
What system are you using? Ubuntu 7.10?  From a LiveCD or already installed on the PC?

---

### Post by boxfullofheads on 2008-03-23
Hi,
I am trying Wubi first because i am new to Linux
i am running WindowsXp Pro
i ran install of Wubi and rebooted i am asked if i want to
boot WindowsXp Pro or Ubuntu i pick Ubunto and it
ran some setup and rebooted then i pick Ubunto
and it shows the Ubunto startup screen then it tells
me Cannot Display This Video Mode and stops

---

### Post by ridgeland on 2008-03-23
Oh...
I've never seen Wubi.
I think that means Ubuntu 8.04 Beta.
If you're new to Linux I recommend you avoid Beta software.  It's released so people that know a lot more than I do can shake it and break it and tell the developers what they did.

I recommend you download and try Ubuntu 7.04 (I like it better than 7.10). Burn it to a CD then boot it as a LiveCD.  If eye-candy is important and you have a new PC with lots of RAM then you'll prefer 7.10.

Wubi is a new idea.  In the past Linux was installed on a separate partition (like C: and D: in the Windows world).  Wubi lets Ubuntu install under XP just like AdobeReader or OpenOffice.  If you need that then please wait until April when 8.04 will be released for general use.

---

### Post by boxfullofheads on 2008-03-23
Hi,
Thank you for your help.. I wanted to try Wubi because it
could be installed like a program and  you did not need to make
partitions.. i have 2 harddrives in my  computer C:\  D:\
WindowsXp is on C:\ and D:\ is empty  so i was thinking
if i like Linux i could put it on D:\ and have WindowsXp and
Linux But i never made a partition before.... When Dell
sent me my computer i had them put in 2 harddrives
I was thinking more space is better.. I have 2 80 GIG
harddrives. I downloaded the .iso file for Ubunto
now i just have to put it on a disk..
I have a DELL Dimension XPS
Pentium 4    3.20GHz    1.00 GB of Ram  GeForce 6800  
Creative SB Audigy sound card

---

### Post by ridgeland on 2008-03-23
Hi,
If you download the iso for Ubuntu 7.10 or 7.04 you can run it as a LiveCD which is somewhat slower but you can see what Ubuntu is like.  You just boot off the CD but don't install anything.  Surf the web without fear of virus and spyware.
Since you have two hard drives you should be able to resize the second one to free some space then install Ubuntu on the freed space.
My practice is to have about 8 - 10 GB for the OS (root) partition.  Far better is to set up two partitions of 8-10 so you can have a keeper OS and a sand box to test another release or version.
Installing to the hard drive adds some data to the Master Boot Record of the first drive.  A program called GRUB will show you a menu each boot and let you choose WinXP or Ubuntu or Another, it defaults per your preference and uses the default if no selection is made in 8 seconds (adjustable).
The LiveCD has partitioning tools that can resize drive 2 and create new partitions, type ext3.
Be sure you have a good backup of the data on drive 2.  I haven't had problems but it's better safe than sorry.

---

### Post by boxfullofheads on 2008-03-24
Hi,
I uninstalled Wubi. I made a liveCD of Ubuntu 7.10 then i booted
from the cd and it showed me some options. i let the time counter
run down and i saw the splash screen for Ubuntu then my screen
went dark and i got Cannot Display This Video Mode...

This is from the LiveCD

---

### Post by ridgeland on 2008-03-24
Ouch.
I hope you're using CD-RWs so you can recycle them.
When you're booting the LiveCD there is an option [F4] to use VGA  try that with something simple like 800x600 and see if you can boot.
Pentium 4... How old is the PC?
There are a couple of other versions to download and try.  You must have DSL and an easy way to download and burn iso images.  Try the simple stuff first though.  What is the monitor you are using?  Could be Ubuntu is assuming a refresh rate that is out of the range of the monitor.  I get that with my old Gateway Crystal Scan 1024.

---

### Post by ridgeland on 2008-03-24
Wow.  While writing a response on this PC and booting Ubuntu 7.10 on my old PC I got the same error message!  I had never seen it before!  I had selected the VGA 800x600 mode and let it boot.  I'm using a Gateway PC that's 5 years old and a Dell LCD monitor.  I did not find a way out of the Cannot Display This Video Mode error message.  Now that I've seen it I'll play with it some more. 
I booted again and it looked like it would boot fine with the default then I got the same error message again!
Now that I see where you are I can try a few things.

---

### Post by ridgeland on 2008-03-24
I tried my Ubuntu 7.04 i386 LiveCD and it booted OK.
I noticed that jaezcurra who started this thread was also having trouble with Ubuntu 7.10 and a Dell monitor.
I also tested Ubuntu 8.04 Beta.  It boots OK.
One more time I see why I stuck with 7.04.  I tried 7.10 but stayed with 7.04.
My recommendation is use 7.04 and be patient for the final release of 8.04 next month.

too many notes but I did just boot 7.10 by setting the video mode [F4] to VGA.

---

### Post by boxfullofheads on 2008-03-24
Hi,
I think my pc is 3 to 4 years old.. i have a DELL E173FP LCD Monitor
I have cox cable internet with a Sisco firewall running and a router
it took me a long time to get my router running... i have my desktop
pc on it and a laptop on it and a XBOX 360 on it

---

### Post by ridgeland on 2008-03-24
The monitor I have trouble with is a Dell model E151FPb.
If you can boot/install using the [F4] option of VGA then once you have Ubuntu installed you can run restricted drivers and have Ubuntu install the Nvidia driver.  I did not have the Dell monitor when I installed Ubuntu on that PC.  When I swapped the monitor I didn't change anything and all seems fine.  If you get it installed make a backup of /etc/X11/xorg.conf like this:
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.firstone
Then if future efforts hose the display you can cp the first one back in.

---

### Post by boxfullofheads on 2008-03-25
Hi,
I looked at my drivers for my video card and found it to be out
of date infact i never updated the video drivers for my video
card so i downloaded the new drivers and installed them
then i booted the Ubuntu LiveCD and it worked.. infact i
am running it now and i am online with it as i write this....
The drivers on my video card had a date of 2004 so that
is when i must have got my computer.. now it has 2007
date for my video drivers.. i am thinking of putting my
Ram up to 2 GiG do you think that will help if i can get
Ubuntu installed...

---

### Post by boxfullofheads on 2008-03-25
Hi,
I have been looking at ubuntu with the LiveCD and i am
suprised it looks like this.. i was thinking you had to
put in all kinds of commands and it was complex and
hard to use.. i told my friends i wanted to try Linux
some day and they told me it was hard to use and
they looked at me like i had 2 heads.. I did not know
anything about a computer when i got my first one
with Windows from walmart  but i got books and i
found out how to use it.. im not a pro but i know
alot more then when i started and infact i bet i know
more then most of my friends now...

---

### Post by ridgeland on 2008-03-25
Congrats.
I've got 2GB of RAM and this PC can hold 4GB.  I watch the ads and say I want another 2GB but then I look at $ free and see I've never touched swap so the next 2GB would give 0 improvement.
I think $ free shows whats been touched more than it shows what is currently being used.  Anyway I seldom see it above 1.5GB. I've read that the time when you need more than 2GB is when you are processing DVDs in RAM, maybe editing full length movies or something.  Maybe remastering LiveDVDs.  I insisted a friend upgrade her XP box from 128MB to 512MB she was shocked by the improvement.  Here you won't get that kind of WOW.  
Watch $ free and see how much swap is being used.  If you aren't seeing much swap used you won't get much bang for the buck.  Still I read the ads and get "RAM envy".

---

### Post by boxfullofheads on 2008-03-26
Hi,
So i would like to try to install Ubuntu. I need a ROOT for the OS
10 GIG and can you tell me about swap space i will need a partition
for that right. can you tell me what i need to do to get this setup.
I would like to make a go at it. i would be thankfull for any help..

I think i may have upgraded my video drivers before but some
time ago my computer would not boot so i had to restore a backup
from a point it would boot and im thinking maybe that gave me back
my old video drivers too, because i think i did upgrade it some time ago.
my computer is set to backup the system files so i can restore it.

---

### Post by ridgeland on 2008-03-26
Here is my strategy for partitions.
double ram, max 2GB for swap partition.
two partitions for OS (Linux) of about 8 to 10 GB each
one partition for Data (Linux) of whatever you want to use.
Of course if you also have Windows thats the first partition.
When you partition I think partition #4 ends up as "Extended" and holds partitions 5-15 (max is 15 not 16).
Each Linux install takes one partition for the OS, uses the swap partition, then you mount (/etc/fstab) the Data partition.
Next time you want to try a new OS (8.10 for example) then use the other Linux partition and if it crashes and burns you still have your first OS intact.
On this PC I have 14 partitions on drive 1 (/dev/sda) and 15 partitions on drive 2 (/dev/sdb).  I've gone from Fedora to SuSE to Ubuntu and still have several version of all three on my PC.  I just installed Fedora 9 Beta this evening.

So how do you do this?
First step is to backup data you couldn't stand to lose.
From the LiveCD run gparted.  Use that to resize partitions and create new partitions. 
Example:
150 GB drive all claimed by WinXP as NTFS
LiveCD - gparted resize partition 1 (WinXP) to just 100 GB.
Click [Apply] (I like doing one step at a time rather than a long list all at once)
In the 50 GB that is now unassigned.
Create partition of 2 GB of type swap (partition #2)
Create partition of 10 GB of type ext3 (partition #3)
Create partition of all thats left (38 GB) as Extended (partition #4)
Create partition of 10 GB of type ext3 (partition #5)
Create rest as 28GB of type ext3 (partition #6) for Data

Then when you install the first Linux tell it to mount "/" on partition #3 (/dev/sda3).  It will find and use the swap. It will leave the rest alone.

Get that far and I'll walk you through mounting the /Data partition automatically in /etc/fstab.

---

### Post by boxfullofheads on 2008-03-26
Hi,
I have been reading all the stuff about installing Ubuntu for a hour
or so, i think before i try installing it i better do some reading
and lern as much as i can. I wanted to ask you is Perl in Ubuntu
i have ActiveState ActivePerl running on my WindowsXp OS

---

### Post by ridgeland on 2008-03-26
Perl 5.8.8 in Ubuntu 7.04 --- searching in Synaptics.  I guess it's standard and not something I added in .  I don't write anything but bash scripts.

---

### Post by boxfullofheads on 2008-03-30
Hi,
I went to install Ubuntu but got a little mixed up on the
partition part i do not want to partition my harddrive that
has WinowsXp on it. the install told me it was going to partition 
disk #1 and i was not sure so i went manul and it shows me

/dev/sda1 fat 16 /media/sda1
/dev/sda2 ntfs /media/sda2     Size Used 46900 MB
/dev/sda3 fat32 /media/sda3

/dev/sdb1 ntfs /media/sdb1     Size Used 3200 MB

i must want the ntfs and i was thinking at booting into
WindowsXp and looking at the size used to find
the drive that does not have WindowsXp on it..
i just do not want to mess this up.

---

### Post by ridgeland on 2008-03-30
I always use Manual Partitioning

> /dev/sda1 fat 16 /media/sda1
/dev/sda2 ntfs /media/sda2 Size Used 46900 MB
/dev/sda3 fat32 /media/sda3

/dev/sdb1 ntfs /media/sdb1 Size Used 3200 MB 

This says you have two hard drives.  sda with three partitions and sdb with one partition.  Since this is a Dell I think that sda1 is a small "Dell Diagnostics" partition.  sda2 is your windows partition. sda3 may show up in Windows as drive D: (CDs etc start at E:  ).  The second drive uses 3.2GB.

Boot the LiveCD.  There run gparted.  In the upper right you can choose which drive to view.  Check them both out.  What total capacity is each drive?  How much of each partition is in use?

---

### Post by boxfullofheads on 2008-03-30
hi,
I do not know how to use Gparted i got a terminal running
and put in sudo fdisk -| and it waited for more input then
i exited and ran the install and a window poped up
Prepare Disk Space
and looking at it in the guided -use entire disk
it shows (sda) 80.0 GB ATA Maxtor
             (sdb) 80.0 GB ATA Maxtor

and the info i sent before was in manual

i realy am new at partitioning i never did it..

---

### Post by ridgeland on 2008-03-31
Sorry I should have explained it better.
Boot the Ubuntu 7.10 CD.  Once you get to the GUI interface
gparted is called something else, my bad.
From the menu at the top:
System -> Administration -> Partition Editor
This runs gparted.  Help -> About shows it as gparted 0.3.3
This is a nice tool to see what partitions exist and how much free space is where.

I reread earlier posts and saw you have two 80GB drives.
I'm not sure what Windows sees.  It could see four partitions and sees two?  Which one(s) doesn't it see?  Note in qparted which drives have how much space in each partition and how much is used.  In gparted the upper right lets you choose drive one (sda) or two (sdb).  Then compare that to Windows -> Windows Explorer (or My Computer) to see the drive's properties (disk size, free space).

OK now you know what exists on the drives.

First if you want to keep any of the 3.2GB that is currently on drive 2 (sdb) then move it over to drive 1 (sda).  I would guess you would be more comfortable doing that in Windows. This frees up all of drive 2 for partitioning.
Partition drive two - use gparted.
Here is what I would do (all in gparted):
partition 1 (sdb1) 2 GB type Swap (or linux-swap?)
partition 2 (sdb2) 10 GB type ext3
partition 3 (sdb3) 10 GB type ext3
partition 4 (sdb4) all thats left (50 GB) as "Extended"
partition 5 (sdb5) a sub-partition of sdb4 10 GB type ext3
partition 6 (sdb6) a sub-partition of sdb4 10 GB type ext3
partition 7 all thats left (about 38 GB) as type ext3.
Why partition?  10 GB is enough for a Linux OS.  The 38 GB will be for Data, things like word documents, pictures, music are not OS dependent and should not be in the OS partition.  When 8.04 gets released install it on sdb3 leaving sdb2 alone.  Over time you will want to try SuSE or Fedora, no problem there is a spare partition and you still have Ubuntu.
How to partition? Delete everything in drive 2 (be sure you're in sdb not sda!)  Click on [Apply] to process the deletes and you should see 80GB free or unallocated.  Then create a new partition.  Now I have to go by memory as I don't have a free hard drive to partition.  Right click on the free space and select create new partition.  The size will show in MB.  Create it as 10000MB and it will show up as 9.77GB (close enough).  Make the ones like above.

I would be more comfortable making a second copy of the good stuff in Windows just in case.  With drive 2 (sdb) set up and ready to go, before installing, you can use the LiveCD and file manager (Nautilus) to copy from drive 1 to the Data partition on drive 2.  You set it up using the terminal and commands.
Open the terminal
$ sudo su
# mkdir /Data
# mount /dev/sdb7 /Data
# mkdir /WinXP
# mount /dev/sda2 /WinXP
# df
df shows what partitions are mounted, free and used space.
So verify that /WinXP and /Data look right.
# nautilus
Now in nautilus you can find in WinXP the good stuff, music, photos, etc and copy them to /Data.  Two settings I prefer is on the left changing [Places] to [Tree] and changing [View as Icons] to [View as List].  Just my preference.

Now you can install Ubuntu, use manual partitioning.  
You'll see a list of the drives (sda and sdb) Click on [x] Format by sdb2.  Then click on sdb2 and [Edit] and tell it to mount "/" (from the drill down options.  It will automatically spot the swap partition and use it.
Install will write GRUB to sda (drive 1), this will be about 512 bytes.  There is also a chance that your BIOS will not allow booting from drive 2!  I have a 2006 Dell that has no problem booting from drive 2.  I have a 2002 Gateway that will not boot from drive 2.  There is a work around it that happens to you.

Have Fun!

---

### Post by boxfullofheads on 2008-03-31
Hi,
Thank you for your help..
Yes what i wanted to do is keep WindowsXp on C:\ and install
Ubuntu Linux on D:\ if i can, that way i would not touch the
drive WindowsXp is on. i was thinking if i needed more room
for files with WindowsXp i could just pick up a USB external
harddrive if i realy needed the space. i took all files off my
2nd harddrive and put them on a USB flash drive for now.
I read alot of books on computer forensics its my hobby
and alot of my books have Linux in them. i need Linux to
try out that part of my books. i have learned alot about
windows this way.

---

### Post by ridgeland on 2008-03-31
Just guessing I would say that 
sda1 = Dell Diagnostics --- if Windows crashes and cannot boot
sda3 = Dell Restore Partition --- to reload Windows OS if needed. probably 3 to 5 GB.

I bet Dell did not give you a Windows OS CD for reinstall.

I checked a book out of the library recently called "Linux Live CDs" by Negus.  It had a double density DVD full of LiveCDs.  One distro was backtrack which was all about testing security.  It might interest you.  

Post back when you get Ubuntu installed and running.

---

### Post by boxfullofheads on 2008-03-31
Hi,
I got Gparted running and it shows all partitions, it is a nice tool.
it shows /dev/sdb1 has 71.49 Gib Unused and 3.00 Gib Used
this tells me this must be the drive WindowsXp is not installed on
I did not know Dell put 3 partitions on my harddrive. I started
buying books on computer security and computer forensics
years ago because my computer was under attack.. things would
pop-up on my screen.. one day a directory called Z___ popped-up
on my desktop and that prompted me to start learning and stop
playing video games. I tracked down the attacker and started watching
them.

---

### Post by ridgeland on 2008-04-01
Did you buy the PC with two hard drives or install the second one yourself?
If it came with the two then I suspect the 3 GB on drive 2 is your only backup Windows OS.  That would be the restore if you ever have to reinstall Windows.
When I see PCs infected by malware I reinstall Windows.  My wife and I always unplug the DSL before booting into Windows.  I even changed boot.ini to prompt us in case we forget.
Be sure you don't loose the 3GB on drive 2.  I'll bet it's your only copy of the Windows OS that you can reinstall.
With the LiveCD you can mount any of the partitions and look at their contents.

---

### Post by boxfullofheads on 2008-04-01
Hi,
I got a bunch of CDs with my computer one of them has
Operating System Already installed on your computer
Reinstallation CD Microsoft Windows XP Professional
Including Service Pack 2.. Sound Blaster Audigy CD
DELL E173FP Color Monitor Drivers and documentation
cd  and a bunch of saftware that my pc came with
but it is a good thing to look at that data and see what
it is.. i know there is a recycle bin.. i can boot up windows
and look at it with a program i have called Directory Snoop
it reads the Master File Tables for both Fat and NTFS
at a cluster level and it can find deleted files. it is a very nice
tool look it up and check it out. you can use it to test programs
that claim to overwrite deleted files and it can do that and purg
the deleted files names in the Master File Table.. you can see
it`s use in computer forensics

---

### Post by ridgeland on 2008-04-01
Sounds like you can reinstall Windows if you have to.  So you're ready to go.
I remember in FAT16 that a deleted file changed the first character to something like * or such and could be recovered.  That was back in DOS 4 and Win3.1 days.  I haven't tried it since.

---

### Post by boxfullofheads on 2008-04-01
Hi
I looked at my 2nd harddrive in explorer and it shows NO files
on D:\  but i opened the drive in Directory Snoop and it shows
a bunch of hidden folders and files. i looked up some of the files
on google and they look like system files for WindowsXp 
system volume information , $MFT , $AttrDef
They look like files for windows to keep track of what is on the
drive and  Default Windows Association...
Directory Snoop Briggs Software
you may be suprised what it finds on your harddrive
stuff you was thinking you deleted long ago..
it has a filter that shows only deleted files
Harddrives, floppy disk , USB flash drives, ZIP drives

---

### Post by ridgeland on 2008-04-01
In Windows Explorer turn on the options to show hidden and system files.  Maybe in Tools -> Folders -> Options then check boxes.
Then you should see that it is either 
System Volume Information
with files like MountPointManager
OR 
Its a full system restore with lots of stuff.

Every drive Windows can see has a hidden "System Volume Information"  so does your C: drive.

---

### Post by boxfullofheads on 2008-04-14
Hi,
I just got Ubuntu running and i am now downloading the 206
updates...

---

### Post by joe68 on 2008-04-19
Folks

I am a bit of a newbie to Linux but have done UNIX courses about 10 years ago. I have installed 8.04 on one desktop in the house but have huge trouble with this one a Dell 9150 - with RAID.  My wireless keyboard and mouse are not recognized and worse when 8.04 finishes loading on Live CD mode, I get the cannot display this mode. But the keyboard comes back to me. When I Ctrl-Alt-F1, the sudo dpkg-reconfigure on xserver.xorg fails too. Any thoughts?  TIA

---

### Post by ridgeland on 2008-04-19
Dell has a bug in the BIOS that causes the USB keyboard to not be available during the initial screen of the boot of the LiveCD.  After the LiveCD boots then the keyboard is available.  Your wireless keyboard probably attaches via USB.  You can probably update the BIOS to solve this, I did on this Dell E520n.
The default CD in 7.10 (maybe 8.04) assumes some ranges that Dell monitors cannot do. Did you try the steps in Post #2?  Look up on line the specs for your monitor, again I'm guessing a Dell monitor.
[http://support.dell.com/support/edocs/monitors/E151FPB/En/specs.htm](http://support.dell.com/support/edocs/monitors/E151FPB/En/specs.htm)
Is the specs page for my monitor.  This shows the range you need for /etc/X11/xorg.conf.  On mine though the horizontal range of 30-61 was still too much.  It would not work until I reduced it to 30-50 like the guess in Post #2.

---

### Post by joe68 on 2008-04-19
Ridgeland, thanks for response.  My BIOS is up-to-date for the Dell 9150 on version A07.  I tried the commands in post 2 previously but tried again as my command line skills come back to me !

However when I cd to /etc, there is no /x11 directory !  So I cannot edit the xorg.conf. Equally when I try the "sudo dpkg-reconfigure xserver.xorg" command, it tells me that xserver.xorg is not installed.  A bit stumped here but it seems that it is something basic that I am overlooking.

---

### Post by ridgeland on 2008-04-19
The directory is /etc/X11
Beware it's case sensitive x11 is not X11.
The file to edit is /etc/X11/xorg.conf
Too bad they mix up X and x like that but oh well.
First though does [Alt]+[Ctrl]+[F1] get you to the $ prompt?  After 
$ sudo su
Can you copy and paste this command at the #:
nano /etc/X11/xorg.conf
Duh... I guess if you cannot use Firefox you cannot copy and paste my bad!
If you cannot then I suspect the install is hosed.  Try again and say if you get to the "Reboot system now" message or if it dies at 92% done or something.

---

