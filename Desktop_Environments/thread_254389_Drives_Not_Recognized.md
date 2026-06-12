---
title: "Drives Not Recognized"
date: 2006-09-09
forum: Desktop Environments
---

### Post by dbjohnson2 on 2006-09-09
I am new to Linux. And new to Ubuntu. I have downloaded Ubuntu 6.06.1 and successfully copied onto a CD. When I boot with the LiveCD inserted the PC boots to Ubuntu. The Ubuntu pre-installed applications seem to run fine. But Ubuntu does not recognize any of the partitions installed on my pair of hard disks. It does recognize USB drives. I have tried reformatting some of the drives on the hard disks from NTSF to FAT32 to FAT without any improvement. 

I have also tried the Freespire OSS LiveCD. It recognizes the various drives without any problem.

Any suggestions on how to get Ubuntu to recognize these drives?

---

### Post by mssever on 2006-09-10
Could you provide the errors you're getting? Ubuntu definitely supports hard drives and USB. Also, have you tried to install, or are you just running off the Live CD?

---

### Post by dbjohnson2 on 2006-09-10
I am just running off the Live CD. I thought installation would add another level of complexity.

After Ubuntu boots up I see 3 icons on the screen: Examples, Install and Drive 1 (the name I assigned to my USB thrumbdrive).
I have downloaded a small variety of file types to this thumbdrive and Ubuntu handles them fine (xls, doc, pdf & jpg).

When I go to Places/Computer I see all my drives but only the thumbdrive has an orange Ubuntu label next to it. 

When I click on one of the the other drives I get the following messages:

     Unable to mount the selected volume.
     error: device/dev/hdb4 is not removeable.
     error: could not mount pmount.

---

### Post by mssever on 2006-09-10
Never tried doing someting like that from the Live CD before. I always mount from the command line (see "man mount" for details). But I think that what's happening is that the menu or whatever is assuming that all partitions that aren't in /etc/fstab are removable disks, and tries to treat them as such. Of course, your hard drive isn't in fstab yet because you haven't installed. Different Distros approach this situation differently.

In short, I would advise going ahead with the install. I don't think there will be any problems with our hard drives, and the installer will give you errors soon enough if there are (and you'll know what you've got some weird and/or bad hardware).


If you install and everything goes fine, you might want to file a bug on launchpad.com.

---

### Post by dbjohnson2 on 2006-09-10
mssever,

Thanks for the response.

I guess I will have to follow your advice. So now I need to figure out how to do it. Using Partition Magic I have set up an partition on the 2nd hard drive to hold Ubuntu. But it is not an active partition so I have to figure out how to make it active.

One final question on the LiveCD approach. Are other people having the problem I described?

---

### Post by rasti121 on 2006-09-10
I had to change my hardware config for Ubuntu to install. For whatever reason I didn't had /dev/hda (which is the first Master drive on the first IDE channel) - I had /dev/hdc -(Master on 2nd channel). I change the cables to the first one and Ubuntu installed nicely.

---

### Post by mssever on 2006-09-10
> **dbjohnson2 said:**
> mssever,

Thanks for the response.

I guess I will have to follow your advice. So now I need to figure out how to do it. Using Partition Magic I have set up an partition on the 2nd hard drive to hold Ubuntu. But it is not an active partition so I have to figure out how to make it active.

One final question on the LiveCD approach. Are other people having the problem I described?
I'm not sure what you mean by an inactive partition. as far as I know, if a partition exists, it's usable--for Linux, anyway. But part of the install process is partitioning. You'll want to choose the manual partition option and make sure that you get what you want. GParted (Ubuntu's partitioner) knows how to set stuff up so that it works for Linux.

---

### Post by dbjohnson2 on 2006-09-15
I took mssever's and after a couple of tries was able to install Ubuntu to the hard drive. But the problem of mounting the hard drives remains. The error message remains the same as in my earlier email. And the sound chord which plays when starting up from the LiveCD no longer plays.

Not exactly sure I am making progress.

Any advice anybody?

---

### Post by mssever on 2006-09-17
> **dbjohnson2 said:**
> I took mssever's and after a couple of tries was able to install Ubuntu to the hard drive. But the problem of mounting the hard drives remains. The error message remains the same as in my earlier email. And the sound chord which plays when starting up from the LiveCD no longer plays.

Not exactly sure I am making progress.

Any advice anybody?

I'm not sure if I correctly understand you. You said that you installed Ubuntu, so it definitely recognizes at least one partition on at least one hard drive--otherwise you wouldn't be able to boot.

Could you describe for me the partitions that you're unable to mount? What format are they? What are the partition numbers (if known; otherwise, on which disk(s) are they?)?

Also, could you post the contents of /etc/fstab?

As far as the sound goes, do you hear any sounds? Go to System > Preferences > Sound and test it. If you don't get any sound, I would recommend starting a separate thread about your sound card. I don't know enough about sound issues to be able to help you there.

---

### Post by dbjohnson2 on 2006-09-17
Perhaps I have mis-stated the problem. Ubuntu sees the drives/ partitions but the enclosed files are not available.

I get the following type of error message(s):

Unable to mount the selected volume.
error: device /dev/hdb2 is not removable

error: could not execute pmount

The PC is a Dell Dimension 8300. It has two hard drives: hda of 60 GB and hdb at 120 GB. Windows XP is installed on hda. When I successfuly install Ubuntu, it also installed onto hda in a new partition.

When Ubuntu boots up, the desktop shows only one drive, the flash drive on which it can access and open various types of files. No other drives/ partitions are shown on the desktop.

Places/Computers shows 8 icons:

CD-ROM/DVD-ROM Drive              no medium found
CD-RW/DVD+RW Drive                no medium found
Boot                              /dev/hda2
Data                              /dev/hdb2
Dell Utility                      /dev/hda1
Generic Storage Device            this is the flash drive
Swap Disk                         /dev/hdb1
File System

There is no media present in the two DVD drives so this is not a problem.
The two hda drives are Windows related. The Ubuntu partition(s) do not show up.
One of the two hdb drives contains all my data files. The Data Drive/ partition is the one I really would like to be able to access from Ubuntu.

Regarding fstab:

I went to Places/Computer/Filesystem/etc. It does not show any Fstab. There are a lot of icons which go from ...emacs, esound, firefox, fonts, foomatic, gaim, gamin ....

No fstab.

---

### Post by dbjohnson2 on 2006-09-17
I noted that I did not respond to your question about the format of the partitions. This info is show below:

Boot                        /dev/hda2              NTFS
Data                        /dev/hdb2              NTFS
Dell Utility                /dev/hda1              FAT
Generic Storage Device                             FAT32
Swap                        /dev/hdb1              NTFS

So, I suspect you may suggest I switch to FAT or FAT32. I have previously tried that with no success when trying to boot from the LiveCD. I will reformat the Data drive to FAT32 and see if it makes any difference. But I am not optimistic.

---

### Post by dbjohnson2 on 2006-09-17
Ok, I have reformatted the Data partition to FAT32. I am still unable to access the files on this drive.

---

### Post by mssever on 2006-09-17
The pmount error is because Ubuntu is confused about your partition for some reason. Fixing /etc/fstab should solve this.

First, what format(s) are your Windows drives? FAT32 or NTFS? Making NTFS drives work properly in Linux is much more difficult than FAT32 partitions--thanks to Microsoft's proprietary specifications.

The Ubuntu partition did show up. Nautilus calls it "Filesystem." Internally, it's known as "/". (Actually, this is only true for the so-called "root partition." Since you have only one Linux partition, it's automatically the root partition.)

Also, /etc/fstab **does** exist on your system. You wouldn't be able to boot without it. Make sure you're looking for a file, not a directory. Because any changes to this file will require superuser privileges, it might be easier to type ```
gksudo gedit /etc/fstab
``` in a terminal window. I need to see the contents of that file in order to help you further. Also, note that Linux is case-sensitive. "Fstab" is not the same as "fstab" or "FsTaB".

---

### Post by mssever on 2006-09-17
Didn't see your posts about the formats. Reformatting to FAT32 was a good idea, but it isn't enough by itself. If it had been FAT32 when you installed, it probably would have worked. But, it can be fixed. My above post still applies.

---

### Post by dbjohnson2 on 2006-09-17
Here is the content of fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Assuming we can resolve this, is there any need to reformat other partitions? It is only the Data partition which I would like to share with Windows.

Thanks for your help.

---

### Post by mssever on 2006-09-17
OK...This shouldn't be too painful. First, create a mount point for your data partition. I'm going to use /media/data here, but you can put it wherever you want and name it whatever you want (I'm not sure off the top of my head how to escape spaces in fstab--better avoid them) as long as it meets the following conditions. It must:[LIST=1]
[*]exist
[*]be a directory
[*]be empty[/LIST]One way to create /media/data is: ```
sudo mkdir -p /media/data
``` 
Next, add the following line to /etc/fstab, changing the appropriate path if you use something other than /media/data (read [FONT=Lucida Console][COLOR=SeaGreen]man fstab[/COLOR][/FONT] and [FONT=Lucida Console][COLOR=SeaGreen]man mount[/COLOR][/FONT] if you want the gory details):
```
/dev/hdb2       /media/data          vfat    defaults,utf8,umask=007,gid=46 0       1
``` 
Now, your partition should be automatically mounted each time you boot. To mount it now without rebooting, type ```
sudo mount -a
``` 
Confirm that it mounted by typing "mount" and looking for the partition in the output.

I believe that this will also create the appropriate desktop icons. If not, you should be able to do this:
```
cd ~/Desktop
ln -s /media/data .
```

---

### Post by mssever on 2006-09-17
> **dbjohnson2 said:**
> is there any need to reformat other partitions? It is only the Data partition which I would like to share with Windows.

No need to reformat. XP prefers to live on an NTFS partition. You can mount it easily enough, but being able to safely write to NTFS is more difficult. However, since your data is on a vfat filesystem (vfat is the Linux name for FAT32), you don't need to worry about it.

---

### Post by dbjohnson2 on 2006-09-17
I made the new directory as you suggested.

But I am uncertain how to add the suggested line to fstab.

I went to places/computer/filesystem/etc and clicked on fstab to open it. I then inserted the line you suggested. There did not appear to be a save option so I attempted to exit fstab. I received the question "The file "etc/fstab" is read only. Do you want to replace it with the one you are saving?" So I selected Replace. Then I received the error message "Could not save the file etc/fstab. You do not have the permissions neccesary to save file"

So what am I doing wrong?

---

### Post by mssever on 2006-09-17
Editing system files requires superuser (root) privileges. AFAIK, there isn't any way to elevate your prvileges from within Nautilus, although there should be. But you can do it from a terminal. Type:
```
gksudo gedit /etc/fstab &
``` gksudo gives you superuser privileges and gedit is a text editor (you can use whichever one you want). You could open a root Nautilus by typing ```
gksudo nautilus &
``` but this is risky since you might forget that you have root privileges and later do something that you'll regret.

---

### Post by dbjohnson2 on 2006-09-17
mssever,

Okay, apparently, with your help, I have got it working.

I entered the gksuko gedit /etc/fstab &  command you recommended.

I received the error meassage "Authentication Rejected, reason: None of the authentication protocals specified are supported and host-based authentication failed."

But the fstab-gedit window opened.

So I entered the line you recommended and saved the new file. Save was now an option whereas it wasn't before.

Upon rebooting, the data drive was accessible.

Thank you for your help.

Can you recommend any good online reference to the Linux commands you have been suggesting?

Thanks again.

Doug

---

### Post by mssever on 2006-09-17
Glad it worked. There are several sources of information:[LIST=1]
[*]sudo/gksudo: These are Ubuntu's way of getting root access. Put sudo before a text-based command and gksudo before a graphical command. Other information you read that is command-line oriented (even this forum) will often tell you that you need to do something as root. That's what these commands are for. You might occasionally see "su" on non-Ubuntu sites, but su doesn't work in Ubuntu by default. Instead, use sudo -i instead of su.
[*][LinuxCommand.org]("http://linuxcommand.org/") is a great introduction to the command line. It's writen for Red Hat/Fedora, not Ubuntu, but almost all of the info applies here, as well.
[*]If you don't know the command for a given task, type ```
apropos keyword | less
``` and you'll get a list of commands/synopses that match the keyword.
[*]Many commands give you quick help if you append --help to the command. For example, ls --help will descibe the options that ls undertands. (ls lists the files in a directory.)
[*]For detailed information about how to use a command, type ```
man command
``` Hit q to leave the viewer.
[*]Finally, there are probably other good resources, but the way I learned the command line was by using it. The first Linux system I used had only the command line interface available, so I was forced to learn it. Now, I still use the CLI because I find it to be faster and easier than the graphical interface for many tasks.[/LIST]

---

