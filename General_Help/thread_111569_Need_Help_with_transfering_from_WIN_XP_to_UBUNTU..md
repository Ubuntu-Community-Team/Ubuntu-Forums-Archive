---
title: "Need Help with transfering from WIN XP to UBUNTU."
date: 2006-01-02
forum: General Help
---

### Post by gytman on 2006-01-02
Hello,

I just learned about Ubuntu after i bought my monthly magazine and they were giving the CD of this OS. Just then my Windows XP lost its mind(as usual) and started showing up error and not open. Then i took my chance and tried out the Cd named Ubuntu. This OS is a magnifecent thing. But my only problem is, i have some important files (mainly TXT) on my C: drive and now i can't see my drive. I wanted to backup those files and remove Windows and completely install Ubuntu on my HDD. Can anyone help me out, cause i am really new to this OS and have newer used it since now.

Thanks in advance :)

---

### Post by Omnios on 2006-01-02
You will have to mount your ntfs partition and copy the files over to the Ubuntu partition as shown in this guide. 

[http://ubuntuguide.org/]("http://ubuntuguide.org/")
[http://ubuntuguide.org/#mountunmountntfs]("http://ubuntuguide.org/#mountunmountntfs")

---

### Post by gytman on 2006-01-02
Is it possible for you to explain to me? English is not my native language and i don't understand those commands written in that guide :(

---

### Post by s_spiff on 2006-01-02
You just made an amazing transition man. I installed Ubuntu about 5 days back [ still have my windows, as my parents find linux very very complex, same with me, but I intend to learn ] , and today I have my net up, have my OS modded to some extent and picking up stuff . And you'll get almost everything in the wiki, and when you can't , you just buzz on here, and people reply in something like 3 minutes and odd! I salute these guys!

---

### Post by Omnios on 2006-01-02
First you must make a directory (file) where the C: drive is accessed 

In terminal type

```
sudo mkdir /media/windows
``` it will ask for your password and enter it and that will mkdir (make directory) called windows

 Then you will have to mount the windows partition by typing this from the terminal

```
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

 You should now be able to open /media/windows and see all the stuff in your windows drive. Now you can make a file in your home folder and should be able to copy and past or drag your windows file to your new folder.

---

### Post by gytman on 2006-01-02
Thanks, i'll try it out. Also how can i make Ubuntu my main and only OS (installing on my HDD)?


EDIT: It's a stupid question, but where is the terminal for Ubuntu. For WINXP it was RUN>CMD :S

---

### Post by Omnios on 2006-01-02
> EDIT: It's a stupid question, but where is the terminal for Ubuntu. For WINXP it was RUN>CMD :S

 Ubuntu has both a run command thing and terminal, accessed from menue/system. The terminal is sort of like a windows doss shell but much much better

---

### Post by jjross on 2006-01-02
to find terminal , just go to applications( top left of screen), accessories, terminal will be listed here

---

### Post by gytman on 2006-01-02
ok i found it :D

---

### Post by gytman on 2006-01-02
Ok i wrote
```
sudo mkdir /media/windows
```

then it showed a blank line.

I rewrote:

```
sudo mkdir /media/windows
```

then it said:

```
mkdir: cannot create directory ' /media/windows': File exits
```

then i wrote the:

```
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

then it said

```
mount: special device /dev/hdal does not exist
```

I didn't get access to my files :(

What is the problem?

---

### Post by Omnios on 2006-01-02
The blank like I think is to type in your password as using the sudo command does the command as root and requires your password. Without the root password it will not have permit ion to make a directory

---

### Post by gytman on 2006-01-02
I didn't have passwords for my Windows accounts. What could the id/pass be?

---

### Post by Omnios on 2006-01-02
Um mounting the ntfs deice has to be done in "Ubuntu" and your sudo password is the same password as the one you use to access your account.

 I hope your not trying to mount your drive in windows and you don't need any windows password stuff to mount it in Linux

---

### Post by gytman on 2006-01-02
I am trying to do this from Ubuntu O/S not WINXP. I logged out from my account to see whether there was any password that i had entered. There seemed to be be only the name 'Ubuntu' logging in, thingy. There were no passwords :(

I just have some files which are word files, and i need them to backup. I'm stuck here :confused:

---

### Post by Omnios on 2006-01-02
When you installed Ubuntu it asked you to create a username and password the password you need to use is that one

---

### Post by jjross on 2006-01-02
Take a look at this link , you might find some answers there.

[http://www.ubuntuforums.org/showthread.php?t=102220&highlight=change+permissions](http://www.ubuntuforums.org/showthread.php?t=102220&highlight=change+permissions)

---

### Post by socrazy143 on 2006-01-02
I think I can clear up some confusion.

The blank line you saw was the command taking place:

```
#  mkdir blah.blah
# 
```

Look familiar?  Yep the directory is there.

As for Windows password I don't think you need it if you are mounting the NTFS but it has been awhile since I played with anything Micro$oft.  You are making a good choice switching.  I just loaded Kubuntu for a customer today and they loved it.

---

### Post by gw90se on 2006-01-02
Why is it saying > mount: special device /dev/hdal does not exist and not hda1? It is showing a lower case L and not the number 1

---

### Post by docmanny on 2006-01-02
What kind of hard drive do you have? If its SATA or SCSI, it should be sda1.
How did you partition your drive? I guess you're using a boot CD, so you haven't installed it to your hard drive yet?

You can see a list of your partitions by typing

sudo cfdisk /dev/sda (for SCSI and SATA)
or 
sudo cfdisk /dev/hda (for IDE)

If you have more than one drive, try sdb or hdb

---

### Post by Swab on 2006-01-02
I think this guy is running from the live CD...

---

### Post by jjross on 2006-01-04
try leaving off the forward slash at the end of windows, like this

sudo mount /dev/hda1 /media/windows -t ntfs -o nls=utf8,umask=0222

---

### Post by Ubluntu on 2006-01-06
/dev/hda1 assumes windows xp was installed on the first partition of the first hard drive.. 
 
If windows was installed anywhere _O_ther then the first partition, the number _1_ will change: /dev/hda_2_
 
If you have 2 hard drives and windows is anywhere on the second drive I believe it's /dev/hd**b**1 ( **b** instead of **a** because its the second drive ) 
 
I'm not sure how to view all the partitions on your drive, but I believe there is a way, and that should help you find the correct /dev/hd**a**_1_
 
good luck, hope this helps you

---

### Post by docmanny on 2006-01-06
You can view all the partitions using gparted (graphically) or cfdisk. You can only view one drive at a time using the text utility though. Just type h to see the help menu.

---

### Post by Frazer on 2006-01-06
This should allow you read only acces to the windows files

Enter into a new Terminal window, if asked for the password enter it

sudo fdisk -l

This should list the partitions 

If you have not allready Created the dir

sudo mkdir /media/windows

Then to mount it (where hda1 is the disk you want to mount of those listed with fdisk)

sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

Then to acces the data open up the home dir and change the address in the address bar to //media/windows

This should be it 

Then to unmount the file system 

sudo umount /media/windows/

This is the easyest way I think to acces the data, I switched to ubuntu myself from windows xp about half a year ago after about a year of trying a few different distros but not finding the right one, and never turned back (well im using Kubuntu mostly now but still the same)

---

### Post by kidcharles on 2006-01-06
[QUOTE=Swab]I think this guy is running from the live CD...[/QUOTE]

I think Swab is right. Given the fact that he never entered a password and he posted this:

[QUOTE=gytman]Thanks, i'll try it out. Also how can i make Ubuntu my main and only OS (installing on my HDD)?[/QUOTE]

---

