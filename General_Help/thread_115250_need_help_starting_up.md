---
title: "need help starting up"
date: 2006-01-10
forum: General Help
---

### Post by RikkiD04 on 2006-01-10
i've been using ubuntu for a while with no problems, but now when i start up, i get this message:

"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

view details (~/.xsession-errors file)"

i have more diskspace and i tried to log on to a failsafe session which failed, oddly enough

please help!!

---

### Post by greenway on 2006-01-10
I fixed this problem by reinstalling the xserver.

---

### Post by RikkiD04 on 2006-01-10
my brother is the computer genius, what exactly is an xserver? and would that erase any data?

---

### Post by greenway on 2006-01-10
Sorry for my short reply...

An xserver is a piece of software that let's you start a X session with one of the desktop environments (Gnome or KDE for example). Reinstalling will not resolve in any data loss what so ever; perfectly safe!

Open the failsafe terminal and type: sudo apt-get remove xserver-xorg. After this is finished type: sudo apt-get install xserver-xorg.

---

### Post by RikkiD04 on 2006-01-10
where would i type that in the failsafe terminal?

---

### Post by RikkiD04 on 2006-01-10
okay, i reinstalled the xserver and have the same problems, now what?

---

### Post by MJSOnline on 2006-01-10
Hi all.

I too am new to Ubuntu 5.10.

I have installed it on my pc, but I am confused.

Ok here goes a list of what I did.

1st hard drive is 9GB
2nd hard drive is 80GB

I put my Windows XP Pro CD into pc, booted off that.
I then made 3 partions on my C: drive, ! for Win XP justt for now, 1 for Ubuntu and 1 for the Ubuntu swap drive.
The 1st partion, Win XP ws formated to FAT32, the rest where left for Ubuntu install Cd/DVD to do.

What I need to know is is the above ok or do I need to take out partions?  How big are they to be?

The second hard drive is unformated for now as I dont know what fileing system to format to using Ubuntu.  Ext2, Ext3 etc, I do not know what they mean.

I have also downloaded programs .tar gz file format, and would like to install them, but do onot know how.

I would like to make "folders" on my 2nd hard drive for downloads, work, pictures etc but dont know how to, again.

What the diffence for desktop installion and Server?  Can I upgrade to Server later or do I need to install Ubuntu from scratch?

Sorry for all the question and long winded list, but I am pulling my hair out.

Can anyone help me?  Many thanks to you all in advance.
Matthew

---

### Post by greenway on 2006-01-10
[QUOTE=RikkiD04]okay, i reinstalled the xserver and have the same problems, now what?[/QUOTE]

Is your home directory still set with the right permissions? This problem can be also be caused by bad home directory permission. Do you have any other users set up on your box? If so, try loggin in with one of these. If this succeeds, you can try correcting the permissions on for the home directory by opening a terminal and typing: sudo chmod 777 /home/<name of the user>

---

### Post by healychan on 2006-01-10
[QUOTE=MJSOnline]Hi all.

I too am new to Ubuntu 5.10.

I have installed it on my pc, but I am confused.............

[/QUOTE]

You don't need the partition for Linux swap spce.
Therefore, you need only 1 for WinXP and 1 for Ubuntu.
If you need to write files from Ubuntu to XP partition, you should use FAT for the XP partition. Because Linux cannot write to NTFS but only read. If not, than use NTFS because it is better.

For your Ubuntu partition, you can use either ext2 or ext3 but ext3 is the lastest.(although may not be the best)

The swap area will be made during installation process. The installer will guide you to do so. If you have more than 512MB RAM, you don't really need much for swap. But make the swap to 256 or more, just in case.

Hope you enjoy the experience of Ubuntu:p

---

### Post by RikkiD04 on 2006-01-10
[QUOTE=greenway]Is your home directory still set with the right permissions? This problem can be also be caused by bad home directory permission. Do you have any other users set up on your box? If so, try loggin in with one of these. If this succeeds, you can try correcting the permissions on for the home directory by opening a terminal and typing: sudo chmod 777 /home/<name of the user>[/QUOTE]


i don't have any other users except allusers and admin or something, but it won't let me log on to anything. i have no idead what the permissions are

thanks for continuing to help me

---

### Post by greenway on 2006-01-10
[QUOTE=MJSOnline]Hi all.

I too am new to Ubuntu 5.10.

I have installed it on my pc, but I am confused.

Ok here goes a list of what I did.

1st hard drive is 9GB
2nd hard drive is 80GB

I put my Windows XP Pro CD into pc, booted off that.
I then made 3 partions on my C: drive, ! for Win XP justt for now, 1 for Ubuntu and 1 for the Ubuntu swap drive.
The 1st partion, Win XP ws formated to FAT32, the rest where left for Ubuntu install Cd/DVD to do.

What I need to know is is the above ok or do I need to take out partions?  How big are they to be?

The second hard drive is unformated for now as I dont know what fileing system to format to using Ubuntu.  Ext2, Ext3 etc, I do not know what they mean.

I have also downloaded programs .tar gz file format, and would like to install them, but do onot know how.

I would like to make "folders" on my 2nd hard drive for downloads, work, pictures etc but dont know how to, again.

What the diffence for desktop installion and Server?  Can I upgrade to Server later or do I need to install Ubuntu from scratch?

Sorry for all the question and long winded list, but I am pulling my hair out.

Can anyone help me?  Many thanks to you all in advance.
Matthew[/QUOTE]

Hi Matthew, 

The easiest way to go about the partitioning is the following: just make a partition for your Windows and leave the rest of the disk unpartitioned. During the installation of Ubuntu you can choose to let Ubuntu use the free space on your hd to install. This is ofcourse under the assumption you will use the rest of the disk for Ubuntu. Are you planning on installing on your 9GB or 80 GB drive? Because 9GB is not going to be enough for installing both Windows and Ubuntu, so I would use the 80GB drive instead. 

The second drive (on which you will not install Ubuntu and Linux) should be a FAT32 drive if you would like both Windows and Linux to use it. If your only planning on letting Ubuntu using it, it should be a EXT3 format.

Since you new to Linux I would suggest waiting with the tar balls (.tar.gz files) for a bit. It's a lot easier to use apt or Synaptic for installing additional software onto your box.

This should get you started, happy Ubuntuing!

---

### Post by brentroos on 2006-01-10
_*_

---

### Post by greenway on 2006-01-10
[QUOTE=RikkiD04]i don't have any other users except allusers and admin or something, but it won't let me log on to anything. i have no idead what the permissions are

thanks for continuing to help me[/QUOTE]

No worries.

When you get your login screen, click the "session" button and select "failsafe terminal" (or something to that order, I am not behind my Ubuntu box right now). After the terminal has opened, type "sudo chmod 777 /home/<the name of your home directory>". If you don't know the name of your home directory, then  type this "sudo chmod -R 777 /home" and try loggin into Gnome or KDE again.

Hope this works for you, I'm off to drink some beers right now, please post your progress and maybe somebody else can continue helping you with this. Anyway, goodluck!

-mattijs

---

### Post by RikkiD04 on 2006-01-10
sorry, i don't understand most of that. my brother usually takes care of my computer but he's not here.  i'm not sure what K3b is and i don't quite understand how to do what you told me i should do

---

### Post by MJSOnline on 2006-01-10
[QUOTE=healychan]You don't need the partition for Linux swap spce.
Therefore, you need only 1 for WinXP and 1 for Ubuntu.
If you need to write files from Ubuntu to XP partition, you should use FAT for the XP partition. Because Linux cannot write to NTFS but only read. If not, than use NTFS because it is better.

For your Ubuntu partition, you can use either ext2 or ext3 but ext3 is the lastest.(although may not be the best)

The swap area will be made during installation process. The installer will guide you to do so. If you have more than 512MB RAM, you don't really need much for swap. But make the swap to 256 or more, just in case.

Hope you enjoy the experience of Ubuntu:p[/QUOTE]

Many thanks Healychan & greenway for your prompt replies.

You are right I do have 512MB of ram, for now, I may upgrade to 2Gb soon  tho.

Should I format the 2nd hard drive to ext3 or do I need to partion it into 2 maybe 3 sections and if so how do I do that?

When going to "Disks" to format 2nd hard drive in Ext3 the drop down shows options, such as /boot, home/ mnt etc.  What are they, what do I choose?

Once I make a back up of my work using Ubuntu can I play/use it on a Windows system?

Does Linux have an "disk defrag" program?  How do I backup programs I have installed via updater etc?

How do I make a folder to save my data in?  If I format the whole drive in ext3 can I reformated back to FAT32 ir NTFS if need be?

Also how do I install my two printers, both have I.P. addresses, in Ubuntu?  One is a Epson R300 the other a HP LaserJet 3320MFD and JetDirect box?

How do I install Epson Print CD to the system, so I can still print to blank printable CD/DVD's?

How do I install, lets say "Azureus" into Ubuntu, as I downloaded it before installing Ubuntu.

Thanks again.
Matthew

---

### Post by RikkiD04 on 2006-01-10
now it says cannot access sudo, chmod or 777 because "no such file or directory exists" can someone else help me too?

---

### Post by dabang on 2006-01-10
> when i start up ubuntu under any session except failsafe terminal, i get this message:

"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

view details (~/.xsession-errors file)"

This happened to me too and it seem's to be a little bug when starting kde apps with *sudo*. It then leaves the ".ICEauhority" file in your home directory with root as owner. So from gdm choose "session" -> "failsafe" login with your standard user an then type:
```
$: sudo chown USERNAME .ICEauthority
```
and
```
$: sudo chgrp USERNAME .ICEauthority
```

Of course, replace "USERNAME" with your username ;-)
You should then be able to login again. Remember: you always have to do this after starting kde-apps with *sudo*...

---

### Post by RikkiD04 on 2006-01-10
[QUOTE=dabang]This happened to me too and it seem's to be a little bug when starting kde apps with *sudo*. It then leaves the ".ICEauhority" file in your home directory with root as owner. So from gdm choose "session" -> "failsafe" login with your standard user an then type:
```
$: sudo chown USERNAME .ICEauthority
```
and
```
$: sudo chgrp USERNAME .ICEauthority
```

Of course, replace "USERNAME" with your username ;-)
You should then be able to login again. Remember: you always have to do this after starting kde-apps with *sudo*...[/QUOTE]
thank you so much, it worked and i'm logged on, but now i get this:

"Your $HOME/.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions."

how do i fix this?

---

### Post by healychan on 2006-01-10
> Should I format the 2nd hard drive to ext3 or do I need to partion it into 2 maybe 3 sections and if so how do I do that?

How many hard disk you have??? What we say hard disk, it mean the things that physically exsit. Partition is something that doesn't really exsit but the computer "think" they are.

Anyway, format the disk/partition to ext3 is a good start. I am using ext3 as well.
Partitioning will perform when you install Ubuntu. I couldn't tell the details since everyone has a different story.
If you need to make more than one partition, then select "manully edit partition table" when you ask to. You can play around with it, modify the table. It will not harm your disk until you save the setting.

> Once I make a back up of my work using Ubuntu can I play/use it on a Windows system?
You can access you file stord on Ubuntu filesystem from WinXP. One popular solution is setting up a Samba server. But this means that you need to learn how to install, configure and maintain Samba. If you are not computer specialist, it could be painful.

> Does Linux have an "disk defrag" program? How do I backup programs I have installed via updater etc?
Sorry I don't know about "disk defrag". Tha programs you installed will be maintain by either Synaptic Package Manager or apt. Once you get installed Ubuntu, come back again and I will show you how to backup.

> How do I install, lets say "Azureus" into Ubuntu, as I downloaded it before installing Ubuntu.
If the files are binary file, you can execute it and installer will start. If it is source file, you need to complie then install it.

There are many resource on this forum. I am sure you can find the answer here. Search for the topic you want to know.

---

### Post by MJSOnline on 2006-01-10
Hi Healyclan.

I have two hard drives. One 9GB, currtly have Windows XP / Ubuntu on it.  The 2nd is unformated bit is 80GB.

I am hopping to make my Epson Print CD software work on Ubuntu.  If I can then goodbye Windows!!

Too say I am overwelled by the amount of "free" software for Linux is an understatement!!

If  put my Ubuntu 5.10 installiuon CD/DVD into my pc at boot up, will it make the partions for me, IF I deleate all the partions on both hard drives and do a clean install of Ubuntu on the 9GB hard drive only?

Thanks again
Matthew

---

### Post by healychan on 2006-01-10
[QUOTE=MJSOnline]Hi Healyclan.

I have two hard drives. One 9GB, currtly have Windows XP / Ubuntu on it.  The 2nd is unformated bit is 80GB.

I am hopping to make my Epson Print CD software work on Ubuntu.  If I can then goodbye Windows!!

Too say I am overwelled by the amount of "free" software for Linux is an understatement!!

If  put my Ubuntu 5.10 installiuon CD/DVD into my pc at boot up, will it make the partions for me, IF I deleate all the partions on both hard drives and do a clean install of Ubuntu on the 9GB hard drive only?

Thanks again
Matthew[/QUOTE]

I think my previous post should answered most of your question. Partitioning will not perform automatically, you need to do some changes depends on how many partition you want. Also you need to choose the type of the partition (ext3, swap etc.....)

One thing about Epson Print CD, what is that for??

---

### Post by MJSOnline on 2006-01-10
[QUOTE=healychan]I think my previous should answered most of your question. Partitioning will not perform automatically, you need to do some changes depends on how many partition you want. Also you need to choose the type of the partition (ext3, swap etc.....)

One thing about Epson Print CD, what is that for??[/QUOTE]

Yes you did, sorry about that. My mistake.

What do Ik use to partion my hard drives then.  I used my Win XP disc before, is that right or is there a Linux package?

The Epson Print CD software is a package to design the face of CD/DVD to then be printed directy to the Cd/DVD using the tray provided.  Pictures and text etc. So it looks nice and easy for cataloging a lot of backups.

Does that help you?

What  about I.P address setting up in Ubuntu for the printers?

Thanks again.  Sorry for being a pain in the neck.
Matthew

---

### Post by healychan on 2006-01-10
> What do Ik use to partion my hard drives then. I used my Win XP disc before, is that right or is there a Linux package?

One of the step in the Ubuntu installer is partitioning. You will be doing it at that stage.

> The Epson Print CD software is a package to design the face of CD/DVD to then be printed directy to the Cd/DVD using the tray provided. Pictures and text etc. So it looks nice and easy for cataloging a lot of backups.

As far as I know, you are not able to run Windows application on Linux. What you can do is to check wil your CD's provider to see if they have a version for Linux. Or you may be able to find some so-called "wrapper" to wrap Windows applications to Linux applications, although the chance is not big. You may also find some application for Linux which doing the same thing as your CD.
I am sorry I can't give you any more advice because all the software in my box are free to download.

---

### Post by MJSOnline on 2006-01-10
Thats fine.  Great help.  Saves me worrying about messing with windows ever again.

Many thanks for your help.

Best regards
Matthew

---

### Post by healychan on 2006-01-10
[QUOTE=MJSOnline]Thats fine.  Great help.  Saves me worrying about messing with windows ever again.

Many thanks for your help.

Best regards
Matthew[/QUOTE]
Just to remind you one thing.
Editing your partition table will not affect the hard disk until you save the changes to the disk. So you can do whatever you like but, think carefully before saving it.

---

### Post by MJSOnline on 2006-01-10
[QUOTE=healychan]Just to remind you one thing.
Editing your partition table will not affect the hard disk until you save the changes to the disk. So you can do whatever you like but, think carefully before saving it.[/QUOTE]

Ok.  Good point.

I am looking at just installing Ubuntu on my C: and poss making two partions on D: one a Ext3 other a FAT32 for backups.

If a new/updated version Ubuntu is released, do IO have to reinstall everything again or just update as normak via CD?

Matthew

---

### Post by healychan on 2006-01-10
[QUOTE=MJSOnline]
If a new/updated version Ubuntu is released, do IO have to reinstall everything again or just update as normak via CD?

Matthew[/QUOTE]
Once you have Ubuntu installed, you can update via an application called "Synaptic Package Manager". It is an user friendly application with powerful features.

I am sure you will love it.;)

---

### Post by LanceM on 2006-01-10
Synaptic is one of the reasons I left Fedora.

---

### Post by greenway on 2006-01-10
[QUOTE=RikkiD04]thank you so much, it worked and i'm logged on, but now i get this:

"Your $HOME/.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions."

how do i fix this?[/QUOTE]


After loggin into Gnome, open a terminal and type: sudo chmod -R 644 /home/USERNAME (replace USERNAME with your username).

---

### Post by garconcn on 2006-01-24
[QUOTE=dabang]This happened to me too and it seem's to be a little bug when starting kde apps with *sudo*. It then leaves the ".ICEauhority" file in your home directory with root as owner. So from gdm choose "session" -> "failsafe" login with your standard user an then type:
```
$: sudo chown USERNAME .ICEauthority
```
and
```
$: sudo chgrp USERNAME .ICEauthority
```

Of course, replace "USERNAME" with your username ;-)
You should then be able to login again. Remember: you always have to do this after starting kde-apps with *sudo*...[/QUOTE]

I have the same login problem. I tried chown & chgrp, but still cannot login. This is the second time with the same problem, I had installed Ubuntu 4 times in this 2 week.:(

---

### Post by garconcn on 2006-01-24
[QUOTE=dabang]This happened to me too and it seem's to be a little bug when starting kde apps with *sudo*. It then leaves the ".ICEauhority" file in your home directory with root as owner. So from gdm choose "session" -> "failsafe" login with your standard user an then type:
```
$: sudo chown USERNAME .ICEauthority
```
and
```
$: sudo chgrp USERNAME .ICEauthority
```

Of course, replace "USERNAME" with your username ;-)
You should then be able to login again. Remember: you always have to do this after starting kde-apps with *sudo*...[/QUOTE]

I have the same login problem. I tried chown & chgrp, but still cannot login. This is the second time with the same problem, I had installed Ubuntu 4 times in this 2 week.:(

---

### Post by garconcn on 2006-01-24
[QUOTE=dabang]This happened to me too and it seem's to be a little bug when starting kde apps with *sudo*. It then leaves the ".ICEauhority" file in your home directory with root as owner. So from gdm choose "session" -> "failsafe" login with your standard user an then type:
```
$: sudo chown USERNAME .ICEauthority
```
and
```
$: sudo chgrp USERNAME .ICEauthority
```

Of course, replace "USERNAME" with your username ;-)
You should then be able to login again. Remember: you always have to do this after starting kde-apps with *sudo*...[/QUOTE]

I have the same login problem. I tried chown & chgrp, but still cannot login. This is the second time with the same problem, I had installed Ubuntu 4 times in this 2 week.:(

---

