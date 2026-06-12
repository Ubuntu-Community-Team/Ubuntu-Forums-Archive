---
title: "LIbreOffice has corrupted a document -any recovery?"
date: 2011-05-04
forum: Desktop Environments
---

### Post by XEtedBear on 2011-05-04
I have a lost the single most important document that I have been working on, using LIbreOffice 3, for the past week. The backups cannot be read by LibreOffice.

Because of the fragility of LibreOfffice I have been saving this document every 30 seconds or so throughout today. I have been able to close this document and re-open it during the day (the process always shows some changes in the document between closing it and re-opening it, but I can usually recover from these changes by redoing the work I did since the last save).

I have just suffered a power-cut here but expected that LibreOffice would be able to recover the document since it was being saved so regularly. When I attempt this LibreOffice tells me that the document is locked by another user. Looking at the directory in which it is stored shows the document to be zero bytes long.

Is it possible that LibreOffice has stored a recoverable copy somewhere?

---

### Post by AndyWise on 2011-06-19
Same thing happened here!

LibreOffice version 3.3.2

Any solution?

---

### Post by atti84it on 2011-07-25
open the libreoffice backups dir:

```
nautilus /home/<username>/.libreoffice/3/user/backup
```

in the terminal

---

### Post by Tristan Schmelcher on 2011-09-03
Happened to me too. It's a bug in LibreOffice. My bug report is at [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/817326](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/817326)

AFAIK it's impossible to recover the document. :(

---

### Post by jim4wb on 2011-09-29
I too have just lost all of my last 2 f***ing days work that i needed to urgently finish tonight. That's the bloody end of librecrap for me. On other occasions i have been able to recover most of my work but it's never going to happen again because i am never going to use the CRAPPY program again

---

### Post by j_iglar on 2011-10-27
Jim4WB - I feel your pain. I've got same issue here. 

It's apparently not JUST a LO issue, but an application failure to deal with the Ext4 filesystem. 
We do not experience this problem with LIbreOffice running on Windows or Mac :(

[Here's a full explanation]("http://www.h-online.com/open/news/item/Ext4-data-loss-explanations-and-workarounds-740671.html") and [here's a workaround ]("http://ezinearticles.com/?How-to-Solve-Zero-Length-File-Problem-in-Linuxs-Ext4-File-System?&id=4240780")we're testing out.

---

### Post by JasonR on 2011-10-27
Does this data loss occur only from power losses?  Has anyone lost data if, say, they're using a laptop or a system with a battery backup?

---

### Post by Mark Phelps on 2011-10-31
> **JasonR said:**
> Does this data loss occur only from power losses?  Has anyone lost data if, say, they're using a laptop or a system with a battery backup?

I've lost data simply due to having to reboot my PC when Unity froze up on me.  

Never had this problem with Open Office.  never had this problem prior to Unity. This 11.10 is the all-time WORST version I've ever seen!

BTW -- the backup folder is EMPTY.  SO much for backups!

---

### Post by Mr.Luz on 2011-11-04
1. Install foremost:
```
sudo apt-get install foremost
```

2. Find out which partition your file was in:
```
sudo fdisk -l
```

3. Create an empty folder:
   i.e. /home/<user>/recovery

4. Recovering with foremost:
```
sudo foremost -t odt -i /dev/sda5 -o /home/francisco/recovery
```
- Replace odt with the file extension you want recover.
- Replace /dev/sda5 with your partition.
- Replace francisco with your userName.
- The recovering may take a while.

5. Check out the recovery folder. You will get a bunch of files named with a sequence of numbers. Find wich sequence belongs to the file you are after by opening up the highest number name of each sequence.

Good luck.

---

### Post by ancaleth on 2011-11-14
Hey,

followed the steps to recovery with foremost, but I am not getting output. When last command is entered into terminal, it doesn't actually do the recovery but shows the command options:

```
ancaleth@buntekuh:~$ sudo foremost -t odt -i /dev/sda2 -o /home/ancaleth/recovery
foremost version 1.5.7 by Jesse Kornblum, Kris Kendall, and Nick Mikus.
$ foremost [-v|-V|-h|-T|-Q|-q|-a|-w-d] [-t <type>] [-s <blocks>] [-k <size>] 
    [-b <size>] [-c <file>] [-o <dir>] [-i <file] 

-V  - display copyright information and exit
-t  - specify file type.  (-t jpeg,pdf ...) 
-d  - turn on indirect block detection (for UNIX file-systems) 
-i  - specify input file (default is stdin) 
-a  - Write all headers, perform no error detection (corrupted files) 
-w  - Only write the audit file, do not write any detected files to the disk 
-o  - set output directory (defaults to output)
-c  - set configuration file to use (defaults to foremost.conf)
-q  - enables quick mode. Search are performed on 512 byte boundaries.
-Q  - enables quiet mode. Suppress output messages. 
-v  - verbose mode. Logs all messages to screen
ancaleth@buntekuh:~$
```

Any ideas...? I need to find an earlier version of the document I now have saved over...

---

### Post by f00fyf00f3r on 2011-12-08
> **ancaleth said:**
> Hey,

followed the steps to recovery with foremost, but I am not getting output. When last command is entered into terminal, it doesn't actually do the recovery but shows the command options:

```
ancaleth@buntekuh:~$ sudo foremost -t odt -i /dev/sda2 -o /home/ancaleth/recovery
foremost version 1.5.7 by Jesse Kornblum, Kris Kendall, and Nick Mikus.
$ foremost [-v|-V|-h|-T|-Q|-q|-a|-w-d] [-t <type>] [-s <blocks>] [-k <size>] 
    [-b <size>] [-c <file>] [-o <dir>] [-i <file] 

-V  - display copyright information and exit
-t  - specify file type.  (-t jpeg,pdf ...) 
-d  - turn on indirect block detection (for UNIX file-systems) 
-i  - specify input file (default is stdin) 
-a  - Write all headers, perform no error detection (corrupted files) 
-w  - Only write the audit file, do not write any detected files to the disk 
-o  - set output directory (defaults to output)
-c  - set configuration file to use (defaults to foremost.conf)
-q  - enables quick mode. Search are performed on 512 byte boundaries.
-Q  - enables quiet mode. Suppress output messages. 
-v  - verbose mode. Logs all messages to screen
ancaleth@buntekuh:~$
```

Any ideas...? I need to find an earlier version of the document I now have saved over...

Yeah you're getting that message because odt is not one of the files you can search for. [https://help.ubuntu.com/community/DataRecovery#Foremost]("https://help.ubuntu.com/community/DataRecovery#Foremost") has the list of file types you can choose from, also able to view this from the man page. Basically it's telling you you're doing something wrong in the command whenever that happens. 

A spreadsheet I was working on randomly got corrupted so I'm working on  recovering it, I'll let you know if I get anywhere =)

---

### Post by eudemus on 2011-12-15
One option that has repeatedly worked for me with corrupted rtf files especially is to download Abiword, open the file in that, then save it as another format from Abiword. Job done.

---

### Post by kurt18947 on 2011-12-15
This is disturbing.  It sounds like an ext4 problem.  I've not had a problem but I believe in the future I'll store copies of significant files on either a USB drive (FAT32) or NTFS partition.  It's good to know this problem is lurking.  As others have pointed out this seems to not happen with L.O. for Windows, just *nix.

---

### Post by vincent.lungwitz on 2012-02-13
Hello ancaleth!

I had the same problem as you and received the same message. I checked out the Ubuntu Wiki ([https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)) and was struck by the fact that they do not list odt files in the foremost section. They propose to look for ole files instead. So, I used the same command as suggested above, but replaced odt with ole. And I did not receive the same message you got, but Foremost worked!

Don't know whether this is still of interest to you, but perhaps to others. Greetings,


Vincent

---

### Post by erotavlas on 2012-03-08
Hi,

I have the same problem with Ubuntu 11.10 and an odf document. The system says 0 byte length. The backup folder is empty and I have already tried with foremost without success. Any suggestions?

Thank you very much

---

### Post by alme on 2012-04-02
Same thing happened to me today.My linux crashed so I had to force shut it down.Before that I had saved my word document many times. When ubuntu reboots I see that the document I had been working with for few hours had 0 bytes on it. Backup file is ticked but there is no file in the backup folder.Run foremost just like described here and it recovered some ppt and xls files but not my opt file.

Can anyone help me please? I had some very important things in that file and I cannt replicate it again.

All the best

---

### Post by LewisTM on 2012-04-03
As a precaution, I'd recommend that users setup their home folder in a separate partition formatted with XFS, if you have the time and knowledge - not a bad investment for keeping precious files intact.

XFS is rock solid and will not behave like this, it's also as fast as ext4 nowadays.

If you go ahead, make sure package xfsprogs is installed. This will ensure mount and fs check tools are available.

---

### Post by gogolink on 2012-04-03
As another precaution:

If you're working on an important file, why not place it in your Dropbox folder? That way, every time you save, it's going to be synchronized with its copy on the Dropbox server.  And whatever happens to your computer, your file should still live in the cloud...

(Added advantage: you can go back to previous versions should you mistakenly save unwanted changes.)

---

### Post by firekage on 2012-11-01
I have the same problem with LO 3.6.0.2 and NTFS filesystem. Under Windows it works, under Ubuntu each time i open a file, do something with it, save it and open up after some other time, LO ask me to recovery file. Don't know what to do. In 

> firekage@deusex:~/.libreoffice/3/user/backup$ 

there is no data to delete or do something with it.

---

### Post by jasob on 2012-11-28
I used the Photorec application, it recovers even overwriten files. 
You can get it from here:
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
That's free tool. Hope you'll be happy.
To protect yourself next time do this in Libre Office:
Go to Tools &#8594; Options and click on Load/Save
In ‘General Settings’ under Load/Save check 'Always create backup copy' box.
God bless
Jack

---

### Post by vasvigupt on 2013-01-30
just waste of time.. you can't recover that document. Libra office is very cheap not trustworthy. lost document third time and now saying bye bye to libra office

---

