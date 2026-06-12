---
title: "Ext2IFS confusion"
date: 2008-12-24
forum: General Help
---

### Post by ozguitarplayer on 2008-12-24
I have Kubuntu on one HHD and Windows on another. On windows I installed Ext2IFS, when I open My Computer Windows recognizes the new Kubuntu drive that I labeled 'Z' however when I try to open Z I only get a message that says that the drive needs to be formatted, so I cannot access the Z drive.

I don't really understand Ext2 in Ubuntu....so my question is.....when Kubuntu is installed on a HHD is it automatically Ext2 or is there something that I should do to make/change it to Ext2?

---

### Post by zvacet on 2008-12-24
If you have Itrepid installed you will have problems,because it look like Ext2IFS doesn´t work in that release.[ Here #9]("http://ubuntuforums.org/showthread.php?t=1015666")

---

### Post by caljohnsmith on 2008-12-24
Intrepid now formats its ext3 partitions to use the newer 256 byte inode size standard, whereas previous versions of Ubuntu used 128 bytes; so as zvacet all ready alluded to, if you are using Intrepid Kubuntu, that is likely your problem, because ext2IFS can't handle the newer 256 byte inode size ext3 partitions yet. There is another program you can use though that can handle the newer ext3 partitions:

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

How about giving that try and let me know how it goes.

---

### Post by ozguitarplayer on 2008-12-24
Thanks zvacet and caljohnsmith,
Yes I am using Intrepid.
I looked at ext2fsd however I am concerned by the warning about possible system crashes, so I'll rethink the need to use it, I'm almost using Kubuntu all the time now and only occassionally in windows.
Since you both have a very impressive number of posts may I ask two other questions....
1. I want to learn about using Terminal (I know almost nothing) and I wonder if there is a site/program that can teach a beginner?
2. I have an external HHD and I cannot access it (it's ntfs and I am using NTFS Config Tool) when I do try to open the drive I get an error message saying...Operation not supported by Mount because NTFS is marked to be in use....
any ideas...?

---

### Post by caljohnsmith on 2008-12-24
> **ozguitarplayer said:**
> 
1. I want to learn about using Terminal (I know almost nothing) and I wonder if there is a site/program that can teach a beginner?
Here are a few websites you could try:

[http://www.linuxcommand.org](http://www.linuxcommand.org)
[http://bash-hackers.org/wiki/doku.php](http://bash-hackers.org/wiki/doku.php)
[http://wooledge.org/mywiki/BashFAQ](http://wooledge.org/mywiki/BashFAQ)
[http://www.linuxconfig.org/Bash_scripting_Tutorial](http://www.linuxconfig.org/Bash_scripting_Tutorial)
[http://bash.cyberciti.biz/](http://bash.cyberciti.biz/)

Some of those sites are more geared toward bash scripting, but you might find some stuff you're interested in. Also, here is a link to some [PDF bash command guides]("http://drop.io/linux_command_refs") that I picked up at some point, but I can't remember where I got them. I think you'll find them useful. 
> **ozguitarplayer said:**
> 
2. I have an external HHD and I cannot access it (it's ntfs and I am using NTFS Config Tool) when I do try to open the drive I get an error message saying...Operation not supported by Mount because NTFS is marked to be in use....
any ideas...?
I would do:
```
sudo fdisk -l
```
Using the above output, determine which is your NTFS partition in the form of sdXY, and then try:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdXY
```
And replace sdXY with the NTFS partition you can't mount. If ntfsfix says it completed successfully, try mounting the partition again, and let me know how it goes.

---

### Post by ozguitarplayer on 2008-12-24
Perfect...thanks heaps caljohnsmith...after a month of trying I can now access the external HHD...and I'll check out the site you listed

---

