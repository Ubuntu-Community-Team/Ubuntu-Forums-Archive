---
title: "Have to boot with previous version of linux!"
date: 2012-02-19
forum: Desktop Environments
---

### Post by ivanchic on 2012-02-19
Hi there everyone!

I have recently installed Xubuntu 11.10 on my lap-top HP Compaq 615/dual boot with Windows XP using Wubi.

Since I did that I usually use Xubuntu and trying to switch completely from WinXP. However, when I turn on my comp and choose Xubuntu from the menu I have problems with starting Xubuntu with linux-3.0.0-16-generic (first option in GRUB menu) because I get only black screen and I have to turn off lap-top using power button. Instead, when I turn it on again, I have to use "Previous version of Linux" option. Then I have an option to choose "Ubuntu, linux-3.0.0.-12-generic" and Xubuntu starts without problems!! I checked in Synaptic and linux-3.0.0.16.19 is labeled as installed.

To be honest, it works well with this but it is really annoying and I was afraid that there are some possible problems with installation! Do I have to worry or are there some explanation for this?

Thanks in advance!

---

### Post by dagroves on 2012-02-19
I have the same  problem but I was installing regular Ubuntu. My computer was not booting  the Linux 3.x kernel correctly. I cannot live book 11.04 or 11.10 of  any of the *buntu family of distros (or any distro that uses the 3.x  kernel). What I had to do was install Ubuntu 10.10 (in your case,  Mythbuntu 10.10) then upgrade to 11.04 and upgrade again to 11.10, then  when you boot, choose an old 2.x kernel in Grub. Then when you get to  the desktop, open a terminal and execute this command 'sudo gedit (or  whatever text editor you use) /etc/default/grub' without quotes or  anything in the (). Then edit the line that says  'GRUB_CMDLINE_LINUX_DEFAULT="quiet splash', after quite and splash add  this 'acpi=off' no quotes. Save the file and exit the text editor, then  in the terminal type this: 'sudo update-grub' and then 'sudo reboot now'  and then choose the 3.x kernel to boot into. It works for me. If you  have any questions feel free to ask and I hope it all works out. It  seems like a lot of trouble, and it is, but it was the only way I could  get anything newer than 10.10 and the 3.x Kernel to run on my old  Pentium 4 PC. Good luck!


(I posted this for Ubuntu, not Xubuntu, but it will work with that one to, it has something to do with the Kernel... it will work, works for me everytime) Good luck!

---

### Post by ivanchic on 2012-02-20
Thanks for reply!

I see that this is a lot of re-installing and other upgrading. However, I don't think that I will have time to do everything you suggested (I am writing PhD thesis now). Especially since system is working with kernel 3.0.0.12. I was just wondering if something is wrong with the laptop itself. You know, it is very painful to write a lot and then lose all your work because of system failure or something similar!

Nevertheless, I will try it after finishing thesis when I expect to have more time for playing with Ubuntu.

---

### Post by Bucky Ball on 2012-02-20
Wubi is:

A/ Not really a dual-boot. It is Wubi. A dual-boot is Ubuntu installed on a separate partition(s) to Windows (side by side);
B/ Not intended as a permanent solution, more to try it out and see if you like (although you can try it out by selecting 'Try Ubuntu' from the first screen presented when you boot from the install CD).

I would deal with the thesis for now (perhaps using Windows if it's stable) and perhaps look into a real dual-boot when you have more time to research it and get it right as 'Wubi is not forever' and definitely NOT intended for production machines (as your machine is; a study workhorse I don't doubt and you need that to be reliable). 

If you do go for the dual-boot, as you are going to need this machine to be rock-solid I suggest you go for 10.04 LTS as the LTS releases are designed for production machines and servers and 10.04 LTS is stable and supported until April 2013. The LTS (long term support) releases have been supported for three years previously but from 12.04 LTS this will be extended to five, as the LTS server versions have always been. 

Even though 12.04 LTS is due out in April I would leave it for six months after then until it gets more stable. You will be able to upgrade directly from 10.04 LTS to 12.04 LTS with one click once it's stable without needing to do a full install. ;)

Incidentally, Xubuntu rocks!

---

### Post by mikodo on 2012-02-20
> **Bucky Ball said:**
>  

If you do go for the dual-boot, as you are going to need this machine to be rock-solid I suggest you go for 10.04 LTS as the LTS releases are designed for production machines and servers and 10.04 LTS is stable and supported until April 2013. The LTS (long term support) releases have been supported for three years previously but from 12.04 LTS this will be extended to five, as the LTS server versions have always been. 

Even though 12.04 LTS is due out in April I would leave it for six months after then until it gets more stable. You will be able to upgrade directly from 10.04 LTS to 12.04 LTS with one click once it's stable without needing to do a full install. ;)

Incidentally, Xubuntu rocks!
FYI, and for accurateness sake, Xubuntu 12.04 for desktops, will be [LTS]("http://ubottu.com/meetingology/logs/ubuntu-meeting/2012/ubuntu-meeting.2012-01-09-20.58.moin.txt"), for [3 years]("http://ubuntuforums.org/showthread.php?t=1893246&page=3"), not 5 years, like Ubuntu 12.04.

Enjoy!

---

### Post by Bucky Ball on 2012-02-20
> **mikodo said:**
> FYI, and for accurateness sake, Xubuntu 12.04 for desktops, will be [LTS]("http://ubottu.com/meetingology/logs/ubuntu-meeting/2012/ubuntu-meeting.2012-01-09-20.58.moin.txt"), for [3 years]("http://ubuntuforums.org/showthread.php?t=1893246&page=3"), not 5 years, like Ubuntu 12.04.

Enjoy!

Wrong. Please see here:

[http://fridge.ubuntu.com/2011/10/21/ubuntu-12-04-to-feature-extended-support-period-for-desktop-users/](http://fridge.ubuntu.com/2011/10/21/ubuntu-12-04-to-feature-extended-support-period-for-desktop-users/)

... and here:

 [http://en.wikipedia.org/wiki/Ubuntu_12.04#Ubuntu_12.04_LTS_.28Precise_Pangolin.29](http://en.wikipedia.org/wiki/Ubuntu_12.04#Ubuntu_12.04_LTS_.28Precise_Pangolin.29)

Please do some research before discrediting information and dispensing the wrong information. You obviously didn't even check the facts. ;)

---

### Post by ManualSparrow on 2012-02-20
> **Bucky Ball said:**
> Wrong. Please see here:

[http://fridge.ubuntu.com/2011/10/21/ubuntu-12-04-to-feature-extended-support-period-for-desktop-users/](http://fridge.ubuntu.com/2011/10/21/ubuntu-12-04-to-feature-extended-support-period-for-desktop-users/)

... and here:

 [http://en.wikipedia.org/wiki/Ubuntu_12.04#Ubuntu_12.04_LTS_.28Precise_Pangolin.29](http://en.wikipedia.org/wiki/Ubuntu_12.04#Ubuntu_12.04_LTS_.28Precise_Pangolin.29)

Please do some research before discrediting information and dispensing the wrong information. You obviously didn't even check the facts. ;)

No, that is correct: [https://en.wikipedia.org/wiki/Xubuntu_12.04#Xubuntu_12.04](https://en.wikipedia.org/wiki/Xubuntu_12.04#Xubuntu_12.04)

XUBUNTU will have a 3-year LTS while regular Ubuntu will have 5. Not that that is especially relevant to the OP anyways - good luck with the thesis!

---

### Post by Bucky Ball on 2012-02-21
> **manualsparrow said:**
> no, that is correct: [https://en.wikipedia.org/wiki/xubuntu_12.04#xubuntu_12.04](https://en.wikipedia.org/wiki/xubuntu_12.04#xubuntu_12.04)



k. ;)

---

### Post by ivanchic on 2012-02-21
Thanks Bucky Ball! I needed that clarification!! I have read a lot about GNU/Linux and Ubuntu before I tried it and this is the simplest explanation about what is and what is not dual boot!

My intention is to move completely to Ubuntu as my only OS both on laptop and office comp. As you said, Wubi is great thing to get start with in switching from Windows. I will certainly apply your advice to install Ubuntu 12.04 in October, hopefully as only OS :D

Thanks guys for your help and your prompt replies!

---

