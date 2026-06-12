---
title: "GUI doesn't load on startup"
date: 2008-08-09
forum: Desktop Environments
---

### Post by Inetrix on 2008-08-09
Well I received my Ubuntu CD a couple days ago. I have been messing with the live demo and I finally decided after a while that I should install it. So I installed it and now whenever I attempt to start Ubuntu (I have dual OS, I'm on my XP right now) I get nothing but the CMD prompt. How can I fix this? I've already tried sudo commands but for some reason it says that sudo doesn't exist... Oh and just to be clear, I'm an absolute beginner with Linux so I'd appreciate detailed instructions on how to fix this. Thank you much!

---

### Post by ad_267 on 2008-08-09
It sounds like Ubuntu wasn't installed properly if it says sudo doesn't exist. I would try reinstalling. Before reinstalling check the cd for defects from the boot up menu on the cd first.

First you could try the command "startx" to try and start the gui and see what that does.
Also "sudo apt-get install ubuntu-desktop" would install the Ubuntu desktop if you could get it to work.

---

### Post by p_quarles on 2008-08-09
Another thing to try, in addition to what ad_267 suggests, is:
```
sudo /etc/init.d/gdm start
```
This should start the login manager that is installed by default with Ubuntu.

For all of these suggestions, be sure to post back any error messages you get here. Likely someone can tell you the next steps to take based on those error messages.

---

### Post by Inetrix on 2008-08-10
well here is the thing. I start it up and it goes from the loading screen (which from the looks of it it doesnt completely load) directly to black screen with letters. When I attempt sudo commands it says sudo does not exist. I tried just removing sudo and it says they don't exist either. I have no error messages when I start it either. It just boots the command screen and thats it.

---

### Post by p_quarles on 2008-08-10
Can you tell us the exact error message - word for word - that you get when typing the command I gave you?

---

### Post by Inetrix on 2008-08-10
lol... it says sudo does not exist. When I try to just go to /etc it says something like acess denied or insufficient privileges. Another thing. Sudo works when I am using the live demo.

---

### Post by p_quarles on 2008-08-10
Sigh. Again, it would be helpful if you could quote the message verbatim rather than paraphrasing.

---

### Post by Inetrix on 2008-08-10
okay.... I'll be right back. Attempting this again.

---

### Post by Inetrix on 2008-08-10
okay I typed

sudo
/bin/sh: does not exist

---

### Post by p_quarles on 2008-08-10
Can you post the output of the following command?:
```
apt-cache policy sudo
```

---

### Post by Inetrix on 2008-08-10
I get this message:

/bin/sh: apt-cache:not found

on a whim I attempted to just access any file with /in front of it and it said:
/bin/sh:/bin: permission denied
is it supposed to do any of this?

---

### Post by p_quarles on 2008-08-10
Well, it sounds like a lot of programs got very badly mangled during the installation process. I was trying to figure out what the root cause was, but at this point it's looking to me like you might want to reinstall. 

One more thing to try, though, that I can think of:
```
ls -l `which sh`
```
Post the results.

---

### Post by Inetrix on 2008-08-10
could my anti-virus/firewall be inhibiting the installation? ill post the results in a second

---

### Post by p_quarles on 2008-08-10
> **Inetrix said:**
> could my anti-virus/firewall be inhibiting the installation? ill post the results in a second
If you mean programs running in Windows, then no. Windows isn't running at all when you install another operating system. 

Unless you are using Wubi, which would be an important detail to include in your problem description. :)

EDIT: If you could post also the output of:
```
cat /etc/passwd
```
that could be helpful as well. We don't really need the whole file, just the line with your username (don't worry -- the name is a relic from UNIX's early days -- it no longer includes any passwords in that file).

---

### Post by Inetrix on 2008-08-10
as far as i can tell I am NOT running wubi. I am installing it off a CD though, not from a downloaded version. I am not attempting to get rid of my windows yet though, I am just trying to get dual OS before I make the complete change. 

oh and the results were:
ls -l 'which sh'
no such file.

---

### Post by p_quarles on 2008-08-10
> **Inetrix said:**
> as far as i can tell I am NOT running wubi. I am installing it off a CD though, not from a downloaded version. I am not attempting to get rid of my windows yet though, I am just trying to get dual OS before I make the complete change. 

oh and the results were:
ls -l 'which sh'
no such file.
Those are supposed to be backticks (the key is on the upper-left of a QWERTY keyboard, and the shift key turns it into ~), not apostrophes/inverted commas. You can also run the same command using:
```
ls -l $(which sh)
```

---

### Post by Inetrix on 2008-08-10
er... I wrote down most of it... but... i kinda gave up because... it was just so much... my hand cramped writing what i did get down:
/bin/sh:which:not found
drwxr-x 8 0       0       13140 dev
drwx--- 2 0       0           0 root
        2 0       0           0 bin
        3 0       0           0 conf
                  0           0 etc
                  0           0 lib
                  0           0 modules
                  0           0 sbin
                  0           0 scripts
                  0        3355 init
                  0           0 var
                  0           0 usr
                  0           0 sys
                  0           0 proc
                  0           0 tmp
                  0           0 cdrom
                  0           0 casper.vars
                  0         781 casper.log
                  0           0 isodevice

---

### Post by p_quarles on 2008-08-10
Well, all I can say is that your installation is pretty massively messed up. Given the references to Casper in the above post, I'm not even sure you did install it -- as odd as this may sound, is it possible that you are still running a live CD?

Anyway, I'd recommend reinstalling. Burn a disk of your own after downloading the file, too, as your installation media may be corrupted.

---

### Post by Inetrix on 2008-08-10
well when I installed I selected install inside windows, that way I didnt delete all of my stuff I have already on my computer. So after about... 20 mins it said that it was installed. I removed the CD and at the OS selection I selected Ubuntu. it gets to the loading screen, the orange bar moves to the right, bounces off and moves backwards until it gets to the middle at which point it turns black and gets to the prompt lol.

---

### Post by p_quarles on 2008-08-10
Ah. 

"Install inside Windows" is the program called Wubi. I don't know enough about that to be able to help.

---

### Post by Inetrix on 2008-08-10
crud. I still need my win xp though because I have some things on here that I dont want to lose. For some reason when I went from my live demo and tried to install it from there it says that I dont have enough room when over half of my HD is empty.

---

### Post by p_quarles on 2008-08-10
You don't have to install "in" Windows to keep Windows. The dual-boot installation works fine for many people. Just make sure you keep all of your data backed up before doing any partitioning.

---

### Post by Inetrix on 2008-08-10
So partitioning seems to be the way to go? Like I said though. I attempted a partition and it told me that I had insufficient space for it. I have somewhere around 41 GB empty right now.

---

### Post by p_quarles on 2008-08-10
Make sure you defragment the drive before partitioning. 41 GB is plenty of space for an Ubuntu partition, so the problem is elsewhere. What tool did you use for partitioning? How many partitions do you currently have?

---

### Post by Inetrix on 2008-08-10
I have no partitions. The installer program asked me how I wanted to install and I said manually. Then it brought me to a screen that asked what I wanted to use: my NTFS disk which was 80GB and thats my entire HD so I went down and said partition and it said I had insufficient space.

---

### Post by p_quarles on 2008-08-10
You need to resize the existing partition and create a new one for the Ubuntu installation. It's not that difficult: just follow the on-screen directions carefully. The Ubuntu download page also has detailed instructions for the process.

---

### Post by Inetrix on 2008-08-10
well I finished my ISO DL but I can't seem to get this program to burn it to a CD. I think Im going to try Wubi again.

---

### Post by Inetrix on 2008-08-10
Well that was epic fail... This ISO burner thing I got from Ubuntu's website doesn't work though.

---

### Post by Inetrix on 2008-08-10
How might I go about partitioning? I'm having a bit of trouble fully understanding what the guide says.

---

### Post by ad_267 on 2008-08-10
You use gparted from the live cd to make partitions. One needs to be a swap partition about the size of your ram and the other for Ubuntu is ext3. Then from the installer you select manual partitioning and select the partitions you created.

---

### Post by Inetrix on 2008-08-10
I have an NTFS formated hard drive though and gparted wont let me edit my free space from that part which is about 90% of my HD space.

---

### Post by ad_267 on 2008-08-11
> **Inetrix said:**
> I have an NTFS formated hard drive though and gparted wont let me edit my free space from that part which is about 90% of my HD space.

You should defragment the drive from in Windows first. Also the drive must be unmounted. You can go into the file manager and right click on the drive and select unmount.

---

### Post by woaibbhemm on 2008-08-12
hello~
    nice   to  meet  you   and     thank  you   for   youe   sharing ,  welcome   to   our   website  !












Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[buy runescape gold](http://www.usfine.com/runescape-c-68.html)sevise.

---

