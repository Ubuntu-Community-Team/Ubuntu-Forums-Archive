---
title: "Im booting into terminal??"
date: 2009-01-13
forum: General Help
---

### Post by Buttink on 2009-01-13
So, I updated to ubuntu 8.10 with the 2.6.27-11. It worked just fine. I turned it off and left. I came back booted it and would getting nothing but a black screen. I then tried every old kernel I had and none would work. So (being new to linux) went into recovery mode and basically ran anything with "fix" in it, lol. So now my machine boots, but I always go straight into terminal, like the gnome ui never starts up or something. Which leads to my question, did I somehow change some config? or is this some weird default boot when a driver fails???? I'll probably just end up reinstalling (using live cd to copy data GO LIVE CD!!), or can I use the install cd to fix it? IDK, but any input would be nice.

---

### Post by Titan8990 on 2009-01-13
Try starting gnome with:

sudo /etc/init.d/gdm start

---

### Post by Buttink on 2009-01-14
Could I have updated to server?? lol

I did what you said and it just says
```
 
 * Starting GNOME Display Manager...                  [OK]

```
then its exactly the same .... man, I boned it good somehow.
I still wonder what I did to it. :shock:

I will add this when I boot i get this weird memssage (or at least i think its weird)
```

kinit: trying to resume from /dev/disk/by-uuid/d6e388ad- .... blah blah
kinit: no resume image, doing normal boot...
```

---

### Post by Titan8990 on 2009-01-14
Try selecting the Ubuntu (recovery mode) from grub. When prompted select the option "fix x"

If not given the option, try this command:


sudo dpkg-reconfigure xserver-xorg

---

### Post by Buttink on 2009-01-14
I did the manual "sudo dpkg-reconfigure xserver-xorg" and tried with both kernel frame buffer and direct hardware communication. Neither fixed the problem. On a side note, when i do "sudo shutdown now" it hang at the very end of the the shutdown.(IDK if this is that sound bug in the sticky thread) But, thought it might be of some importance......

Um, what else can i think of? I know one of my machines didn't like installing something and exited the updater without removing packages. But, I don't think that was this one. Can i just rerun the 8.1 updater?

---

### Post by Titan8990 on 2009-01-14
You need to give shutdown and additional argument:

sudo shutdown -h now

h = halt or power off


> Can i just rerun the 8.1 updater?


Yes, but when possible it is recommended to a fresh install instead of updating.

---

### Post by Buttink on 2009-01-14
....dam you guys and you smartness :D the -h worked btw

Yah, I think i'm just going to get the live cd out and just copy my home folder and reinstall not like its that hard.

---

### Post by batido on 2009-01-14
I am having a very similar problem!!!  How would I copy my home folder?

---

### Post by Buttink on 2009-01-14
I havent actualy tried this yet so dont quote me on it. But, I believe, if you boot from the live cd, you can access your harddrive and then copy to a flash drive however you like. I dont know enough about the terminal commands, but I bet we could actualy do it though the terminal on boot.

---

### Post by albinootje on 2009-01-14
> **batido said:**
> I am having a very similar problem!!!  How would I copy my home folder?

You want to back up your /home to some usb disk or stick ?
Boot from the Ubuntu installation cdrom, chose the "live session" without installing.
Attach the usb-disk or usb-stick.
Open Nautilus as root :
```

gksu nautilus

```
Copy /home completely to your usb drive.

Beware that if you're using a FAT32 or NTFS formatted usb drive, then it is advised to make an archive of your /home in order to prevent the permissions of your /home backup being messed up completely.
You can create an archive by right-clicking on the /home folder within Nautilus (the default file manager of Ubuntu).

---

### Post by batido on 2009-01-14
> **albinootje said:**
> You want to back up your /home to some usb disk or stick ?
Boot from the Ubuntu installation cdrom, chose the "live session" without installing.
Attach the usb-disk or usb-stick.
Open Nautilus as root :
```

gksu nautilus

```
Copy /home completely to your usb drive.

Beware that if you're using a FAT32 or NTFS formatted usb drive, then it is advised to make an archive of your /home in order to prevent the permissions of your /home backup being messed up completely.
You can create an archive by right-clicking on the /home folder within Nautilus (the default file manager of Ubuntu).
Ok, things are working.  I am using the LIVE CD.  I can see my home folder it is sitting in an area called disk-1.

The problem is, when I go to archive the file to my USB drive, it says that I do not have permission.  How do I become root for the disk-1 partition if I am using the LIVE CD?  Or how do I get permission?  Also, when it asks to archive it gives me a number of choices, like .zip or tar.gz.  What is that?  And which should I choose?  Also, when I finally copy the home folder to my USB drive and re-install UBUNTU.  How do I "unarchive"  the home folder on my USB?  I apologize for all the questions, but I really don''t know much about linux.  I am trying my best,

---

### Post by albinootje on 2009-01-14
> **batido said:**
> Ok, things are working.  I am using the LIVE CD.  I can see my home folder it is sitting in an area called disk-1.

The problem is, when I go to archive the file to my USB drive, it says that I do not have permission.  How do I become root for the disk-1 partition if I am using the LIVE CD?  Or how do I get permission?  

If you did start "gksu nautilus" from a terminal, you should have all the permissions you need. Did you do that ?
> 
Also, when it asks to archive it gives me a number of choices, like .zip or tar.gz.  What is that?  And which should I choose?  

Choosing tar.gz is fine (tar and gzip are both archivers). And if the zip and unzip are also available, then you can choose that if you prefer.
The overall end result should be the same for this operation.

> 
Also, when I finally copy the home folder to my USB drive and re-install UBUNTU.  How do I "unarchive"  the home folder on my USB?  I apologize for all the questions, but I really don''t know much about linux.  I am trying my best,

The unarchive should be simply a double-click on the archive (again from "gksu nautilus", and then extract into /

---

### Post by batido on 2009-01-15
for some reason nautilus would not let me archive the home folder or the user name folder under the home folder.  but it did let me archive the desktop folder and my documents folder which was a huge help, because a lot of those files required permission and could be transferred to my USB by a simple copy command.  Thank you so much for your help.

thats all i really need.  ill just install ibex now and pray things work. sigh.  thanks again albinootje

---

### Post by albinootje on 2009-01-15
> **batido said:**
> for some reason nautilus would not let me archive the home folder or the user name folder under the home folder.  

That's weird :(
> 
but it did let me archive the desktop folder and my documents folder which was a huge help, because a lot of those files required permission and could be transferred to my USB by a simple copy command.  Thank you so much for your help.

thats all i really need.  ill just install ibex now and pray things work. sigh.  thanks again albinootje

You're welcome. 
Hopefully it will all be fine after the reinstall.

---

