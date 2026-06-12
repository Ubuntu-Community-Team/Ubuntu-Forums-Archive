---
title: "Grub error 22"
date: 2009-06-01
forum: General Help
---

### Post by TxsFireman on 2009-06-01
I have a Toshiba Laptop that came with Windows XP.  A couple of years ago I had a friend help me dual boot Ubuntu with XP.  After dealing with some problems with Ubuntu and rarely using it, I have decided to go back to Windows XP.  So as you are reading this and laughing at my expense I'm sure you can tell I'm far from an advanced user.  I saved all my important files on an external hd and formatted the hd in my laptop using the recovery cd that came with my computer.  After it was complete I removed the disc and restarted the computer to find Grub error 22.  I cant use the hd in my laptop, but I can explore it as an exernal hd via usb no problem.  I have formatted it and reinstalled the recovery disc a couple of times, but I'm sure you all know that isn't working.  I'm wondering if there is a way to delete the grub files so I can get back to life as it were.  The solutions I have found online require me to be logged in on either XP or Ubuntu to fix.  I can't log on at all on the hd as my primary drive, only as an external hd via usb, wich won't allow me to follow the solutions I have found.  Please help.  Thank you.

---

### Post by ptsubin on 2009-06-01
Put a windows XP installation CD inside. Boot from CD, Then after all loaded, choose recovery mode. You will get a console and then just give the command fixboot and then fixmbr. Reboot your system and boot from hard disk. Grub will be gone and your XP will boot.

---

### Post by TxsFireman on 2009-06-01
Maybe I am not understanding your advice, but I am not able to enter any command prompts at any point during the recovery cd.  I can't use the hd as a primary in my laptop.  All I get is Grub error 22.  I can access the bios menu which is how I am able to boot from the cd.  This is the options I have while booting from the windows recovery cd:

MENU
Please select:
1. Install Express Media Player
2. Proceed with Recovery CD
Please select option 1 or 2. [1,2]?

I'm not sure what the Media Player is but I've tried it and it's a dead end.  Gives me an error message and I have to shut down the computer...so I press 2

Now it gives me a warning about how this process will restore the original default system and delete any data I have on the hd.  It says to enter F1=OK, F2=Cancel
So I enter F1...

Then one more warning about how I'm about to delete the contents of my drive...
To continue press (C).  To abort press (A)...[C,A]?
I enter C...

The computer restarts itself and proceeds with the recovery process.  The first time I ran this it gave me options to delete the extra partition which I did.  It now only recognizes the single partition.  It runs Toshiba Restore Tool 7.5.1 for about 30 min and says to remove the cd and hit any key.  I do that and it then restarts and right after the Toshiba logo comes on then off the screen it says Grub Error 22 and my only option is to do a hard restart.

Please let me know if there is something I'm doing wrong.  Thank you.

I have also tried all of the function keys during boot up but I can only access bios.  Thank you.

---

### Post by mhgsys on 2009-06-01
Try a real windows Installation cd instead of a recovery cd.
and follow @ptsubin

---

### Post by raymondh on 2009-06-01
Hello TxsFireman,

You can use a windows disk or the ubuntu LiveCD.  Should you try the ubuntu liveCD, you need to know firsthand which partition the windows OS is .... note, this is not the windows recovery partition ....

To use liveCD:

Boot into a live session
Open a terminal (applications > accessories > terminal)
Type and enter one at a time

```
sudo apt-get install ms-sys
ms-sys --mbr /dev/hd? 
``` 

where ? is the partition of windows

and Reboot.

Regards,

---

### Post by TxsFireman on 2009-06-01
Thank you to everyone who has offered their knowledge and expertise.  Due to my fairly limited experience with Ubuntu I am going to try to pursue what appears to be the "easy route" and try to get a windows xp installation cd.  I was told that since I bought the computer with XP on it I technically bought the rights to XP and therefore should be able to contact the manufacturer and request the installation cd to be mailed to me for free.  I'm told that they don't include the installation cd with the computer because few people ever need it and it was a way to cut costs.  Sounds good on paper, but I was told by Toshiba customer support that they only offer the recovery cd which is what I already have. So before I go barking up Microsoft's tree does anyone know if there is any truth to this or am I going to be better off trying to grow one in a petri dish using the stem cells from an unborn recovery disc?  Any information would be very helpful.  Thank you all.

---

### Post by raymondh on 2009-06-02
> **TxsFireman said:**
> Thank you to everyone who has offered their knowledge and expertise.  Due to my fairly limited experience with Ubuntu I am going to try to pursue what appears to be the "easy route" and try to get a windows xp installation cd.  I was told that since I bought the computer with XP on it I technically bought the rights to XP and therefore should be able to contact the manufacturer and request the installation cd to be mailed to me for free.  I'm told that they don't include the installation cd with the computer because few people ever need it and it was a way to cut costs.  Sounds good on paper, but I was told by Toshiba customer support that they only offer the recovery cd which is what I already have. So before I go barking up Microsoft's tree does anyone know if there is any truth to this or am I going to be better off trying to grow one in a petri dish using the stem cells from an unborn recovery disc?  Any information would be very helpful.  Thank you all.

With DELL, I asked for and got a install disk for free.  I told them I accidentaly deleted the recovery partition and c drive when I was trying to learn the windows disk management tool to try to create a separate media/data partition.  This was partly true, by the way.  Hence my preference towards gparted now :)

Good luck

---

### Post by TxsFireman on 2009-06-02
So I called Toshiba to request an installation cd and was informed that no such animal exists.  Furthermore I was basically treated like an idiot by the Tech guy...even though there is some truth to that...he still shouldn't have acted that way.  I told him that I know whats wrong with my comp. and that I need an installation disc, not a recovery disc, to fix it.  He said in so many words that since the majority of the people that buy Toshiba are not capable of installing software that way(ie: stupid), so Toshiba "dumbed it down" to a recovery disc.  He then tried to convince me that he knew what was wrong with my comp. and after a couple of bad guesses he said my hd was bad.  
Soooo, he could have been somewhat sympathetic and nice, but he felt the need to convince me that he's a genius and I'm....not.  I won't be buying Toshiba again...
So, I tried calling Microsoft and was told that they sell the software to Toshiba and they change it or modify it or whatever so anything that Microsoft could give me would not be compatible.  Another dead end.  
So, after todays conversations, I have convinced myself to give Ubuntu another go.  
As we speak, I have booted from my old Ubuntu disc with the faulty hd in the laptop.  I followed Raymond's advice and here's what I get:
ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys
ubuntu@ubuntu:~$ ms-sys --mbr/dev/hd
The program 'ms-sys' is currently not installed.  You can install it by typing:
sudo apt-get install ms-sys
You will have to enable component called 'universe'
bash: ms-sys: command not found
ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys
ubuntu@ubuntu:~$ 

Again I would like to thank everyone for the help I've been given and any help you might give in the future.  Thank you.

---

### Post by raymondh on 2009-06-02
[http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)

There's a good FAQ on that page.

Here's another method ... much simpler IMHO

[http://www.nerdden.com/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.nerdden.com/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

Let us know how goes :)

---

### Post by TxsFireman on 2009-06-02
FYI, I'm running Ubuntu 7.10 and I'm having an issue getting the ms-sys to work...as a matter of fact, when I follow the instructions by going to the software sources and enabling universe repositories, it tries to install a ton of updates but they are all unable to be installed and I keep getting "Couldn't find package ms-sys"  I've tried to follow several fixes for this on other threads but I can't get it to work.  I wonder what I'm doing wrong, or is there an issue with this fix and 7.10?

---

### Post by raymondh on 2009-06-02
I cannot figure out why you can't get ms-sys ... let me do some google-fu vis-a-vis 7.10.

Have you tried nerden's method ... the second link?

Regards,

---

### Post by TxsFireman on 2009-06-02
I'm sorry for the long post, but I hope this helps everyone see what I've tried to maybe eliminate some duplication.  I can't seem to get past step 2 of the nerdden instructions.  Thank you all for sticking with me on this.

ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys
ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys
ubuntu@ubuntu:~$ tar -xzvf ms-sys*.tgz
tar: ms-sys*.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
  404 Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
  404 Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys
ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys
ubuntu@ubuntu:~$ sudo apt-get install ms-sys

---

### Post by raymondh on 2009-06-02
Am re-reading the whole thread and need a clarification ...

1.  You no longer have any ubuntu in your HD and are using the liveCD right now to communicate.

2.  Our goal is to restore windows's MBR.  I ask because GRUB and its' error 22 is a linux-based bootloader which has overwritten the windows' MBR when you dual booted some years ago....

---

### Post by raymondh on 2009-06-02
Thanks for that ....

am not sure if gutsy and its' repos are still supported.  Can you make a liveCD of 8.04 or 8.10?

am still googling "FIX WINDOWS MBR USING UBUNTU LIVECD" ...

---

### Post by TxsFireman on 2009-06-02
...Also, I don't know if this matters, but I'm not trying to "save" anything on this hd. I have all my important stuff safe and sound on an external hd.  This hd that I basically screwed up is my 250GB that I would like to use as my primary.  I have a 100GB that I usually use in an enclosure as an external hd, but for now I have used the restore cd and have XP up and running on it.  I am running off of the Ubuntu 7.10 live cd right now with the messed up 250GB in.  Basically, I just wanted to make sure you know that I'm not trying to save any information on the drive so if there is any other fix out there that might work I'm all in.  Again, I really do appreciate your time.

---

### Post by TxsFireman on 2009-06-02
Yes, my 100GB drive is fully functional, I will try that if you think it will help.

---

### Post by raymondh on 2009-06-02
> **TxsFireman said:**
> ...Also, I don't know if this matters, but I'm not trying to "save" anything on this hd. I have all my important stuff safe and sound on an external hd.  This hd that I basically screwed up is my 250GB that I would like to use as my primary.  I have a 100GB that I usually use in an enclosure as an external hd, but for now I have used the restore cd and have XP up and running on it.  I am running off of the Ubuntu 7.10 live cd right now with the messed up 250GB in.  Basically, I just wanted to make sure you know that I'm not trying to save any information on the drive so if there is any other fix out there that might work I'm all in.  Again, I really do appreciate your time.

Cool ... am glad you have a system running.  So our goal is to restore the windows MBR in the 250.  Let's do another try.  Kindly download supergrubdisk.  Here's the link.  Herman is also a forum member.

[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

Herman's documentation is very thorough .... kindly read which part is appropriate for our cause :)

Boot into the supergrub disk, select windows and tell it to fix windows startup.  Oh, use the 250 HD ... so that means you have to use either the liveCD to download and burn the disk or, use the 100 HD to do the download and then transfer back to the 250.

Just out of curiosity, using liveCD and the 250, can you post an output of gparted as well as

```
sudo fdisk -l
```

Thanks.

---

### Post by raymondh on 2009-06-02
> **TxsFireman said:**
> ...Also, I don't know if this matters, but I'm not trying to "save" anything on this hd.

am also glad about this :)

---

### Post by raymondh on 2009-06-02
Another option is to boot up the 100HD windows and tell it to make a rescue CD.  Look in the administrative section.  Go back to the 250 and boot into the rescueCD you just made and use it to repair ... getting a command prompt and fixmbr.

This is assuming that both are running the same version of windows.

Hope that helps.

---

### Post by lindsay7 on 2009-06-02
FYI, from what I have read > ms-sys, is no longer available. Something to do with micorsoft not allowing it any longer.

---

### Post by TxsFireman on 2009-06-02
Thank you for the tips, I'm gonna have to sign off for now, I'll give them a shot tomorrow, I need to spend some family time right now.  Thanks for all your help.

---

### Post by TxsFireman on 2009-06-04
I would like to thank everyone for helping me fix my problem.  I did get it fixed using my operable XP on another hd to make a boot cd and restore the mbr files.  Everyone here has been so helpful and patient with me and I really do appreciate it so much.  Especially after I was treated like a lowlife by Toshiba.  Thank you all.

---

### Post by Vined Adobo on 2009-06-04
Please disregard this post.  It was supposed to be to the Vista forum.

---

### Post by raymondh on 2009-06-04
> **TxsFireman said:**
> I would like to thank everyone for helping me fix my problem.  I did get it fixed using my operable XP on another hd to make a boot cd and restore the mbr files.  Everyone here has been so helpful and patient with me and I really do appreciate it so much.  Especially after I was treated like a lowlife by Toshiba.  Thank you all.

Am glad you are up and running :)  As a side note, do try to download and burn the supergrubdisk.  That and a copy of gparted are invaluable tools.

Congratulations again.

---

