---
title: "Ext2 driver in Windows 7"
date: 2009-01-18
forum: General Help
---

### Post by JoeCool1986 on 2009-01-18
Hey there fellow Windows 7 beta testers. Has anyone gotten a dual-boot system to work where Windows 7 can recognize your ext2/3 partitions? I installed Ext2 IFS (from [http://www.fs-driver.org/](http://www.fs-driver.org/)) and it works exactly like it did in Vista and XP, except that it forgets to assign drive letters every reboot. So I have to go into the control panel and assign the drive letters every time I boot into windows.

Any help?

---

### Post by DeMus on 2009-01-18
> **JoeCool1986 said:**
> Hey there fellow Windows 7 beta testers. Has anyone gotten a dual-boot system to work where Windows 7 can recognize your ext2/3 partitions? I installed Ext2 IFS (from [http://www.fs-driver.org/](http://www.fs-driver.org/)) and it works exactly like it did in Vista and XP, except that it forgets to assign drive letters every reboot. So I have to go into the control panel and assign the drive letters every time I boot into windows.

Any help?

Is this a Ubuntu or a Windows forum? Write an e-mail to [email]Bill@microsoft.com[/email] and ask for help.

:)   :)   :)   :)   :)   :)   :)   :)

---

### Post by niteshifter on 2009-01-18
Hi,

I'll give the same answer I would to a paying client: Win 7 is beta. Beta as applied to software means "we know it's broken but don't know where yet".

Congrats - you've found something broken. The folks at fs-driver.org would want to know. MS might actually want to know about this. But I rather doubt they read these forums looking for QA reports on their product, after all MS has their own forums for Win 7, plus a quick google shows many, many more. Such as the Other OS here in Ubuntu-land.

Just sayin' you need to fish where they're bitin' is all ;)

---

### Post by JoeCool1986 on 2009-01-18
Actually, I've done multiple searches on google trying to find a solution, but anything dealing with both ext2/3 and Windows 7 is few and far between. Also, I have searched windows 7 forums looking for answers but the vast majority of people seem far more interested in windows specific hardware/software issues than anything linux related, like ext2. So, I concluded that I would return to where I first heard about the windows ext2 driver - this forum.

But you're right, I will at least contact the makers of the driver, because obviously they would probably like to be aware of this issue.

---

### Post by eleifsp on 2009-02-23
You got it to read the file system?  Better than I can get;  Windows 7 will mount my EXT3 file systems, but asks me to format it every time I want to access it (that, and it unmounts at reboot XD).

As for mounting at restart, [here's]("http://www.fs-driver.org/faq.html#mountvol") an FAQ from their site on writing a command prompt line to mount your drive.  If you put that in a batch script (*.bat) and place that script in your startup folder in the start menu, it'll load when you log in.

---

### Post by JoeCool1986 on 2009-04-20
eleifsp, while I never solved my problem, I know the solution to yours. Somewhere around the end of last year the default inode size for ext3 filesystems was changed from 128 bytes to 256 bytes. So if you installed Hardy fresh, I think you probably got the new size. Unfortunately, the ext2 driver (from fs-driver.org) doesn't support 256 bytes. So, if you want it fixed, you'll have to move all your files to a temporary location, format a new Ext3 partition with inode size of 128 bytes (probably using linux terminal programs from the LiveCD would be best), and then move all your files back.

But before you go to all that trouble, use mountdiag.exe from [http://www.fs-driver.org/troubleshoot.html](http://www.fs-driver.org/troubleshoot.html) to make sure that is your problem.

---

### Post by Nachowarrior on 2009-07-25
"Is this a Ubuntu or a Windows forum? Write an e-mail to [email]Bill@microsoft.com[/email] and ask for help."

"Hi,

I'll give the same answer I would to a paying client: Win 7 is beta. Beta as applied to software means "we know it's broken but don't know where yet".

Congrats - you've found something broken. The folks at fs-driver.org would want to know. MS might actually want to know about this. But I rather doubt they read these forums looking for QA reports on their product, after all MS has their own forums for Win 7, plus a quick google shows many, many more. Such as the Other OS here in Ubuntu-land.

Just sayin' you need to fish where they're bitin' is all "


Since when is this a forum for pompus assholes with no useful information?
Your posts have absoloutly no value. Go to a forum that wants useless comments if you just want to stuff your nose in the air at people that need help. 

As for the original poster, I just got the last rtm version up and running, i'll let you know what i can do with the ext2ifs driver in a later post.

---

### Post by diggedy on 2009-07-25
> **eleifsp said:**
> You got it to read the file system?  Better than I can get;  Windows 7 will mount my EXT3 file systems, but asks me to format it every time I want to access it .

I have this same problem in windows 7, vista and even XP. Im yet to get any windows access my ext3 drives :/

---

### Post by JoeCool1986 on 2009-07-25
(deleted)

---

### Post by Nachowarrior on 2009-07-30
"Digital signature and can be overridden in windows 7 RC by pressing F8 repetably during startup.
You will then enter the menu where you can choose safe mode.
At the bottom of that menu you can override digital signature."

Taken from another forum i'm going to try and install in safe mode with compaitbility for vista. See if that solves the issue. Another issue I have run into with this driver is the fact that my tv tuner softwares will not write to an ext2 device and the status of my files/folders will not change from "read only" even though they are not secured as such and are writeable. This makes it very annoying for programs that adhere to the windows setting rather than just trying to write to it anyway. Anywho, That's all i've got so far. I'll keep you up to date.

btw i'm working on win 7 ultimate x64 build 7600

---

### Post by x33a on 2009-07-30
hi, firstly you should definitely let the developers at fs-driver know about the issue.

secondly, you could give this a try

[http://sourceforge.net/projects/ext2fsd/](http://sourceforge.net/projects/ext2fsd/)

it has better features in my opinion and is more customizable. i have been using it without any problems for a while.

i switched to it because fs-driver doesn't support inode size of 256 bytes.

---

### Post by jrochet on 2009-08-02
> **x33a said:**
> hi, firstly you should definitely let the developers at fs-driver know about the issue.

secondly, you could give this a try

[http://sourceforge.net/projects/ext2fsd/](http://sourceforge.net/projects/ext2fsd/)

it has better features in my opinion and is more customizable. i have been using it without any problems for a while.

i switched to it because fs-driver doesn't support inode size of 256 bytes.

I can confirm that running ext2fsd (Ext2Fsd-0.48.exe) in Windows 7 x64 RTM (7600.***) works.  I was messing with fs-driver's app first and so my .exe is set with Windows Vista compatibility mode, and run as administrator checked, plus I'm booted into the mode with the digitally signed driver force thing bypassed.

Those things might not even need to be in place for ext2fsd to work, I just had them like that because of the need in ext2ifs.

---

### Post by egalvan on 2009-08-03
> **x33a said:**
> hi, firstly you should definitely let the developers at fs-driver know about the issue.


The authors  are aware of this problem.

Quote from their own:

Release Notes of Ext2 IFS version 1.11a

>  Large inodes

The current version of Ext2 IFS only mounts volumes with an inode size of 128 like old Linux kernels have.

Some very new Linux distributions create an Ext3 file systems with inodes of 256 bytes. Ext2 IFS 1.11 is not able to access them.

Currently there is only one workaround: Please back up the files and create the Ext3 file system again. Give the mkfs.ext3 tool the -I 128 switch. Finally, restore all files with the backup. 


Perhaps if more of the folks using this fine driver would be willing to donate a couple of bucks...

I started using this back in April 08, when Hardy came out.
It worked well, so I donated $5.

---

### Post by x33a on 2009-08-03
@ egalvan,

actually i was referring to the problem the OP was facing.

about the inode problem, i too, got to know about it from the developers' faq.

---

### Post by Bealer on 2009-09-13
EXT2IFS will only support inode of 128.

EXT2FSD will support inodes of upto 256.

Neither support "true" EXT4 although I think EXT2FSD will still support a converted EXT3 to EXT4 (ie not "true" EXT4) partition though.

Figure out which partition you want to look at

```
sudo fdisk -l
```

The check it's current inode value

```
sudo tune2fs -l /dev/sda7 | grep Inode
```

And then to format a partition with inode of 128:

```
sudo mke2fs -i 128 -j -t ext3 /dev/sda7
```

I'm running Window 7 RC x64. EXT2FSD won't run, but I can get EXT2IFS running just fine. The only thing is upon rebooting it forgots the assigned drive letter, so I have to reassign it. I'm working on a fix for that though.

And when running .exe file it throws a permission error. I think I fixed that when I had Vista ages back, but can't remember how.

---

### Post by ivancamilov on 2009-09-28
after a little tweaking, I finally got it to work. I use EXT2IFS, can't tell you if it works also with EXT2FSD.

You'll first have to make sure your partition has an inode size of 128 (you can follow Bealers steps to make sure). Once you have formated your partition properly, boot Windows and install EXT2IFS. Hit next a couple times, and when it finishes you should be able to access the files in your partition.

If Windows asks you to format the partition, you'll have to double check your inode size. Also, if you have an EXT3 partition you need to make sure Ubuntu shuts down properly (the FAQ explains it better than I could [http://www.fs-driver.org/faq.html#acc_ext3](http://www.fs-driver.org/faq.html#acc_ext3)).

If you can access your files, next step is creating a .bat file, otherwise you´ll need to assign a drive letter every time Windows restarts. I based my solution in the FAQ ([http://www.fs-driver.org/faq.html#acc_ext3](http://www.fs-driver.org/faq.html#acc_ext3)), and [eleifsp]("http://ubuntuforums.org/member.php?u=452034") reply. What you do now is fire up a command window (Windows+R->cmd) and type

```
mountvol X:\ /L>ext2ifs.bat
```Where X:\ is your EXT2/EXT3 drive. Is VERY IMPORTANT that you do this before restarting (ie. when the drive letter is assigned). Next you have to open the explorer and go to the URL in the prompt (usually, C:\Users\Your_User_Name). There should be a file called ext2ifs.bat. Right-Click->Edit, and you´ll see a the label Windows asigns to the volume. add mountvol X:\ before that, so that it looks like this:

```
mountvol X:\ \\?\Volume{HERE_IS_THE_LABEL}
```Save and close. Now right-click->create direct link, and copy the direct link to your start folder (you can find it clicking on the start button->all programs). Finally, hit right-click->properties in the direct link, go to the "direct link" tab, advances, and let it run as administrator.

Lastly, go to the control panel->user accounts->Change user account control and disable it. Not the greatest thing to do (or actually, it is) but this won't work unless you turn off UAC.

That's it. Next time you reboot, you should have your drive properly mounted. I hope everyone understands, my english isn't that good.

---

### Post by DeMus on 2009-09-28
> **Nachowarrior said:**
> "Is this a Ubuntu or a Windows forum? Write an e-mail to [email]Bill@microsoft.com[/email] and ask for help."

"Hi,

I'll give the same answer I would to a paying client: Win 7 is beta. Beta as applied to software means "we know it's broken but don't know where yet".

Congrats - you've found something broken. The folks at fs-driver.org would want to know. MS might actually want to know about this. But I rather doubt they read these forums looking for QA reports on their product, after all MS has their own forums for Win 7, plus a quick google shows many, many more. Such as the Other OS here in Ubuntu-land.

Just sayin' you need to fish where they're bitin' is all "


Since when is this a forum for pompus ******** with no useful information?
Your posts have absoloutly no value. Go to a forum that wants useless comments if you just want to stuff your nose in the air at people that need help. 

As for the original poster, I just got the last rtm version up and running, i'll let you know what i can do with the ext2ifs driver in a later post.

The reason I gave that answer is simple: it is a question about a beta version of a Windows product. The Op states he has visited Windows forums to find help, but they don't want to mess with Linux.
Why should this forum be transferred into a Windows forum? If people want to use that OS let them, it's there choice, but don't come wining here if things don't work. Soon we will solve every Windows problem here.
I, and I'm sure many more, come here to seek help when needed and to give help when possible about Ubuntu problems.
Hope I made my first answer clear now.

---

### Post by ivancamilov on 2009-09-28
> **DeMus said:**
> The reason I gave that answer is simple: it is a question about a beta version of a Windows product. The Op states he has visited Windows forums to find help, but they don't want to mess with Linux.
Why should this forum be transferred into a Windows forum? If people want to use that OS let them, it's there choice, but don't come wining here if things don't work. Soon we will solve every Windows problem here.
I, and I'm sure many more, come here to seek help when needed and to give help when possible about Ubuntu problems.
Hope I made my first answer clear now.

I think you're using the wrong OS my friend. Ubuntu is all about the people -regular folks, those who aren't as computer savvy as you. You know, Linux for human beings; the #1 bug in Ubuntu is "Microsoft has a majority market share". So clearly, by being as helpful as you can with the people who are still trying out Ubuntu while they have Windows you´ll show them that we're an open community and they'll eventually make the switch (hey, eventually that's what got me).

This IS a problem related to Ubuntu; if you cared only for Windows, you wouldn't have an EXT2/3 partition, now would you?.

If you have a problem helping Ubuntu users solve their problems, then you should try another distro, because you are just scaring people off, and making the #1 bug in Ubuntu harder to resolve.

---

### Post by soccermonster5 on 2009-10-30
> **ivancamilov said:**
> after a little tweaking, I finally got it to work. I use EXT2IFS, can't tell you if it works also with EXT2FSD.

You'll first have to make sure your partition has an inode size of 128 (you can follow Bealers steps to make sure). Once you have formated your partition properly, boot Windows and install EXT2IFS. Hit next a couple times, and when it finishes you should be able to access the files in your partition.

If Windows asks you to format the partition, you'll have to double check your inode size. Also, if you have an EXT3 partition you need to make sure Ubuntu shuts down properly (the FAQ explains it better than I could [http://www.fs-driver.org/faq.html#acc_ext3](http://www.fs-driver.org/faq.html#acc_ext3)).

If you can access your files, next step is creating a .bat file, otherwise you´ll need to assign a drive letter every time Windows restarts. I based my solution in the FAQ ([http://www.fs-driver.org/faq.html#acc_ext3](http://www.fs-driver.org/faq.html#acc_ext3)), and [eleifsp]("http://ubuntuforums.org/member.php?u=452034") reply. What you do now is fire up a command window (Windows+R->cmd) and type

```
mountvol X:\ /L>ext2ifs.bat
```Where X:\ is your EXT2/EXT3 drive. Is VERY IMPORTANT that you do this before restarting (ie. when the drive letter is assigned). Next you have to open the explorer and go to the URL in the prompt (usually, C:\Users\Your_User_Name). There should be a file called ext2ifs.bat. Right-Click->Edit, and you´ll see a the label Windows asigns to the volume. add mountvol X:\ before that, so that it looks like this:

```
mountvol X:\ \\?\Volume{HERE_IS_THE_LABEL}
```Save and close. Now right-click->create direct link, and copy the direct link to your start folder (you can find it clicking on the start button->all programs). Finally, hit right-click->properties in the direct link, go to the "direct link" tab, advances, and let it run as administrator.

Lastly, go to the control panel->user accounts->Change user account control and disable it. Not the greatest thing to do (or actually, it is) but this won't work unless you turn off UAC.

That's it. Next time you reboot, you should have your drive properly mounted. I hope everyone understands, my english isn't that good.
Worked for me, thanks.  But I didn't have to create any links whatsoever, I just placed the .bat file into my startup folder.

---

### Post by chrisinspace on 2009-11-10
I want to second ivancamilov's post.  People shouldn't forget that we are members of a community.  In my mind, that is the thing that sets FOSS apart from commercial software.

I worked on this issue for hours.  I was following the steps from the [ext2ifs FAQ]("http://www.fs-driver.org/faq.html#mountvol") to the letter.  I had no problems getting the device ID or creating the batch file, but whether I ran the command directly from the command line or ran my batch file, the command just ran continuously with no results until I killed it with CTRL+C.  I finally figured out it was due to one missing space at the end of the line.

So instead of:
```
mountvol X:\ \\?\Volume{HERE_IS_THE_LABEL}
```

It should be :
```
mountvol X:\ \\?\Volume{HERE_IS_THE_LABEL}<space>
```

So, if you are copying code and then modifying it with the values specific to your system, be sure to leave one space after the close bracket ( **}** ) character.

---

### Post by domi007 on 2010-03-25
Sorry bringing up an old topic, but I have Ext2FSD installed on my Windows 7, and it works awesome, but...sometimes it just simply crashes my system with "BAD_POOL_HEADER" Blue Screen of Death...

Anyone experienced the same?

Thanks,
DOMy

mod: I am sorry guys, I just found the solution...should have used Google a little bit more carefully..
[http://www.deobfuscate.net/?p=514](http://www.deobfuscate.net/?p=514)

---

### Post by taur on 2010-06-11
> **eleifsp said:**
> You got it to read the file system?  Better than I can get;  Windows 7 will mount my EXT3 file systems, but asks me to format it every time I want to access it (that, and it unmounts at reboot XD).

As for mounting at restart, [here's]("http://www.fs-driver.org/faq.html#mountvol") an FAQ from their site on writing a command prompt line to mount your drive.  If you put that in a batch script (*.bat) and place that script in your startup folder in the start menu, it'll load when you log in.

this [http://www.ext2fsd.com/](http://www.ext2fsd.com/) driver supports the newer ext 256 byte inode

---

