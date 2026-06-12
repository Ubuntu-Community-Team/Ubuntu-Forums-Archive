---
title: "mounting hda and hdb drives on desktop"
date: 2005-09-05
forum: Desktop Environments
---

### Post by geovino on 2005-09-05
Can someone please tell me how to show my hda1 drive (winXP) and hdb6 (linux) drives so I can access the files! This is the reason I have tried to use Ubuntu in the pass and went to another distro. But I would like to use Ubuntu if I can access my hard drives.

Thank you

---

### Post by Christoff UK on 2005-09-05
I guess you could create a folder say Windows on the desktop, open terminal then do  - sudo mount /dev/hda1 /home/[USER NAME]/Desktop/Windows . I suspect there is a better way of doing it, that will work if it is Fat32, not sure about NTFS, and then for the HDB6, do the same but change the folder names and use /dev/hdb6...

O yeh you need to put it in /etc/fstab like the guy said below...

---

### Post by KingBahamut on 2005-09-05
Youll have to edit your fstab to reflect the automount of your NTFS drive (your XP drive). 

[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

read all that first. 

as far as accessing your ubuntu drive from your windows system, forget all hope of that happening.

---

### Post by geovino on 2005-09-05
thanks, I'll read it, but why can't they put it there like so many other distros? it shouldn't be this difficult. Kanotix, Knoppix, Mepis have all been easier to use. What makes Ubuntu so popular? I would like to know. Thanks.

---

### Post by Christoff UK on 2005-09-05
Well it's just ....its just very hard to explain, but for a lot of people it just feels right,with apt-get and to me ubuntu seems logical, and went through many distros before ubuntu and its the only one that I've ever stuck, something about it keeps drawing me back

---

### Post by mcrofutt on 2005-09-05
Sorry to butt-in, but I've been wondering the same thing about my hdc1. It's a Kanotix distro. (That way I don't have to muck up my Ubuntu with Kde)  :) 
 May I assume the same applies for ANY other drive one may want mounted at boot with read/write access?
 
 Thanks for the info!

---

### Post by geovino on 2005-09-05
[QUOTE=Christoff UK]Well it's just ....its just very hard to explain, but for a lot of people it just feels right,with apt-get and to me ubuntu seems logical, and went through many distros before ubuntu and its the only one that I've ever stuck, something about it keeps drawing me back[/QUOTE]
 Tha'ts how I've felt about Mepis for the past six months. It just had more apps preconfigured that I would use. I'm sure that Ubuntu is equally as good, just different. 

I would like to understand the way to mount drives. I haven't been able to get it to work. Many have mentined to edit the  fstab file, but what do I add to it? and where is it located? 

Thanks

---

### Post by arnieboy on 2005-09-05
[QUOTE=KingBahamut]as far as accessing your ubuntu drive from your windows system, forget all hope of that happening.[/QUOTE]
u can access an ext2/ext3 partition from windows.
refer to: [http://ubuntuguide.org/#readlinuxpartitionsinwindows](http://ubuntuguide.org/#readlinuxpartitionsinwindows)

---

### Post by arnieboy on 2005-09-05
[QUOTE=geovino]Tha'ts how I've felt about Mepis for the past six months. It just had more apps preconfigured that I would use. I'm sure that Ubuntu is equally as good, just different. 

I would like to understand the way to mount drives. I haven't been able to get it to work. Many have mentined to edit the  fstab file, but what do I add to it? and where is it located? 

Thanks[/QUOTE]
when u are asked to read [http://ubuntuguide.org](http://ubuntuguide.org) please make the effort to read it. we dont keep ranting the same thing over and over again for no reason. since u havent read it, u still dont know where the fstab file lies. please try to understand our problem. we are a bunch of 20 odd experts here trying to help ten times our number of newbies and 5 times the number of intermediate users to help them get around ubuntu and linux in general every day. if u keep asking questions without bothering to read what we suggest, we end up wasting our time spoonfeeding you. Since, this is not an RTFM forum, people tend to over-test our patience at times. Please dont do that. Its a request.

---

### Post by Christoff UK on 2005-09-05
Well here is what you need to do for you NTFS partition...

Into the terminal...

mkdir /home/[your user name]/Desktop/Windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

Then add the following into the end of the file...

/dev/hda1       /home/[USER NAME]/Desktop/Windows  ntfs    nls=utf8,umask=0222 0       0


That should mean the partition will be mounting at boot up, all this information was obtained off the ever handy [Ubuntu Guide](http://ubuntuguide.org/#automountntfs)

---

### Post by geovino on 2005-09-05
[QUOTE=arnieboy]when u are asked to read [http://ubuntuguide.org](http://ubuntuguide.org) please take the effort to read it. we dont keep ranting the same thing over and over again for no reason. since u havent read it, u still dont know where the fstab file lies. please try to understand our problem. we are a bunch of 20 odd experts here trying to help ten times our number of newbies and 5 times the number of intermediate users to help them get around ubuntu and linux in general every day. if u keep asking questions without bothering to read what we suggest, we end up wasting our time spoonfeeding you. Since, this is not an RTFM forum, people tend to over-test our patience at times. Please dont do that. Its a request.[/QUOTE]
 Sorry about that. I have read the part about mounting files. I entered this at the command line:
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
but it didn't work for some reason, I was in root terminal not the regular one. maybe that was the problem.

---

### Post by Christoff UK on 2005-09-05
What went wrong? What doesnt work?

O hang on you need to enter into fstab like I said in my earlier post and then do sudo mount -a or just reboot

---

### Post by artinla on 2005-09-05
"thanks, I'll read it, but why can't they put it there like so many other distros? it shouldn't be this difficult. Kanotix, Knoppix, Mepis have all been easier to use. What makes Ubuntu so popular? I would like to know."

Geovino,

Having used most of the distributions mentioned, I feel qualified to answer your question.  The answer in a nutshell is support.  Mepis is a very good operating system, I am especially fond of the desktop based install, a "try and fly" method that is unique.  I also like the repair tools such as the XFree repair.  It is a well thought out distro.  The trouble with Mepis is that infighting between the guy who created it and the people who support and promote it is causing the distro to suffer.  Things such as some want xorg and others want to stay with xfree.  The future is dim for Mepis.  The support boards are filled with Linux Tech wanna-be's most of whom come here for help.  It is hard to get a straight answer there.
Knoppix is also pretty good, except that I happen to be a Gnome fan and Knoppix is KDE based.  Correct me if I am wrong, but I believe Knoppix is a "LiveCD only" distro, so I don't think it is reasonable to try to compare it to Ubuntu.
RedHat (Fedora), Mandrake, Suse, etc are all RPM based and for that reason alone are nightmares to update/upgrade.  The future is in APT or Autopackage based distributions that can be maintained and upgraded by the average PC user who is used to Windows.  In my opinion, bringing over this type of user is the only way Linux will ever be a viable desktop option OVER windows.

I have tried them all, and the support and knowledge available here is utterly amazing.  There is nothing that can't be done in Ubuntu, provided that you have the initiative to try it, and the ability to formulate the right questions to ask here.
Don't let the Peter T. Breuer's of the world scare you away from asking questions here, this community is eager to help.  That is why I use Ubuntu, and why many others have joined me in the last couple years.   You can waste your time trying all the other distros, or you can load Ubuntu and never look back.  Good luck.

Art

---

### Post by arnieboy on 2005-09-05
[QUOTE=geovino]Sorry about that. I have read the part about mounting files. I entered this at the command line:
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
but it didn't work for some reason, I was in root terminal not the regular one. maybe that was the problem.[/QUOTE]
open up a terminal and do the following:
paste the contents of 
```
sudo fdisk -l
```
and
```
cat /etc/fstab
```

---

### Post by geovino on 2005-09-06
[QUOTE=artinla]"thanks, I'll read it, but why can't they put it there like so many other distros? it shouldn't be this difficult. Kanotix, Knoppix, Mepis have all been easier to use. What makes Ubuntu so popular? I would like to know."

Geovino,

Having used most of the distributions mentioned, I feel qualified to answer your question.  The answer in a nutshell is support.  Mepis is a very good operating system, I am especially fond of the desktop based install, a "try and fly" method that is unique.  I also like the repair tools such as the XFree repair.  It is a well thought out distro.  The trouble with Mepis is that infighting between the guy who created it and the people who support and promote it is causing the distro to suffer.  Things such as some want xorg and others want to stay with xfree.  The future is dim for Mepis.  The support boards are filled with Linux Tech wanna-be's most of whom come here for help.  It is hard to get a straight answer there.
Knoppix is also pretty good, except that I happen to be a Gnome fan and Knoppix is KDE based.  Correct me if I am wrong, but I believe Knoppix is a "LiveCD only" distro, so I don't think it is reasonable to try to compare it to Ubuntu.
RedHat (Fedora), Mandrake, Suse, etc are all RPM based and for that reason alone are nightmares to update/upgrade.  The future is in APT or Autopackage based distributions that can be maintained and upgraded by the average PC user who is used to Windows.  In my opinion, bringing over this type of user is the only way Linux will ever be a viable desktop option OVER windows.

I have tried them all, and the support and knowledge available here is utterly amazing.  There is nothing that can't be done in Ubuntu, provided that you have the initiative to try it, and the ability to formulate the right questions to ask here.
Don't let the Peter T. Breuer's of the world scare you away from asking questions here, this community is eager to help.  That is why I use Ubuntu, and why many others have joined me in the last couple years.   You can waste your time trying all the other distros, or you can load Ubuntu and never look back.  Good luck.

Art[/QUOTE]
 Thanks for the info. It's too bad about the situation at Mepis. It's been working well for me. But I've been curious about Ubuntu and wanted to try it out. I'm only using the breezy-live CD ver.510. So making changes would have to be put on a usb memory stick. Personally I haven't cared for Gnome, but I can get used to it. I will practice more with the live-cd until I feel ready to do a HD install.

Thanks again for your feedback and it's good to know that your forum is very good.

---

### Post by geovino on 2005-09-06
[QUOTE=Christoff UK]What went wrong? What doesnt work?

O hang on you need to enter into fstab like I said in my earlier post and then do sudo mount -a or just reboot[/QUOTE]
 will this work with the live-cd?

---

### Post by Christoff UK on 2005-09-06
No because you dont have a premnament file system i dont think? Therefore you cant make the drive appear on boot up, or so i would imagine, you should try installing ubuntu.

---

### Post by Irony on 2005-09-06
See this thread;

[http://ubuntuforums.org/showthread.php?t=62074&highlight=viewing+linux+partitions](http://ubuntuforums.org/showthread.php?t=62074&highlight=viewing+linux+partitions)

I created some folders in my media file to mount windows partitions. If you want them on the actual desktop I suppose there is a relatively simple way to add a shortcut (link) from the desktop to these media files.

---

### Post by geovino on 2005-09-21
[QUOTE=arnieboy]when u are asked to read [http://ubuntuguide.org](http://ubuntuguide.org) please make the effort to read it. we dont keep ranting the same thing over and over again for no reason. since u havent read it, u still dont know where the fstab file lies. please try to understand our problem. we are a bunch of 20 odd experts here trying to help ten times our number of newbies and 5 times the number of intermediate users to help them get around ubuntu and linux in general every day. if u keep asking questions without bothering to read what we suggest, we end up wasting our time spoonfeeding you. Since, this is not an RTFM forum, people tend to over-test our patience at times. Please dont do that. Its a request.[/QUOTE]
 Ubuntu guide has been down, know when it's coming back? 

I'm still very curious about Ubuntu...I'll try the 5.10 preview live cd today. I won't expect to see the hda winxp drive, that still is a problem. I have not been able to find the /etc/fstab file on the live cd, maybe it's not there.

Any clues? Thanks

---

### Post by celticmonkey on 2005-09-27
After you have sorted out your fstab as the others have explained, you might want to check out this help item from the unofficial ubuntu guide:

[http://ubuntuguide.org/#showdesktopicons](http://ubuntuguide.org/#showdesktopicons)

By default, the destkop icons for mounted volumes you like are turned off in ubuntu. That might help you turn them on again.

---

