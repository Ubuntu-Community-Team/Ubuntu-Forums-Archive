---
title: "Installing UBUNTU"
date: 2010-05-29
forum: Desktop Environments
---

### Post by minhajmsm on 2010-05-29
Hi guys,, im new in here, and I have been using ubuntu for a certain period of time on a assembled system, and now I have a SAMSUNG system,,, when i try to install ubuntu - when i select install or try without..... all I get is a black screen and a cursor blinking..!!!!! :confused: ... so far Ive tried 8.10 DVD, 9.04 CD, 9.10 CD ,,,, all are same.... pls anyone help me.....

---

### Post by sidzen on 2010-05-29
If you don't mind my asking -- what is your system and what was on the hard drive you wish to install to?

---

### Post by hok00age on 2010-05-29
> **minhajmsm said:**
> Hi guys,, im new in here, and I have been using ubuntu for a certain period of time on a assembled system, and now I have a SAMSUNG system,,, when i try to install ubuntu - when i select install or try without..... all I get is a black screen and a cursor blinking..!!!!! :confused: ... so far Ive tried 8.10 DVD, 9.04 CD, 9.10 CD ,,,, all are same.... pls anyone help me.....

Try alternate version of Ubuntu ISO. You can download it at the Ubuntu.com. The alternate version use text user interface so it's recommended for low-level graphic machine.

Hope this will help :)

---

### Post by minhajmsm on 2010-05-29
cpu - 3.0 GHz / VGA - NVIDIA 128MB/8x / HD - 40GB(3-4 years old)512RAM can be upgraded to 1GB - 512x2 >>> but I tried a Hitachi 40GB, still was the same, been installing the same version the 8.10 for every person who wants it.. but cant in my system... recently installed to a DELL Notebook as well... pls.... I WANT UBUNTU INSTALLED IN MY SYSTEM, even I tried Fedora core 6 o 7 I guess.... all end up same.....

---

### Post by sidzen on 2010-05-30
I was delayed installing an OS on another HD, so apologise.
An associate of mine had trouble with a Hitachi hard drive going "**** up" for no apparent reason --
he found that its "life" was pre-determined by either HP or Hitachi, and that installing ubuntu on it made it "die."
I'm wondering if you're having a similar problem with Samsung.
You may want to blank the HD with zeros using either dban or dd, if not done already, before attempting 
to install again.

And, as [hok00age]("http://ubuntuforums.org/member.php?u=782482") suggested, the *alternate* version is a good idea.

---

### Post by minhajmsm on 2010-05-30
whats the difference with the software than deleting the partition by fixing it to another system????? completely delete all the partitions and start installing ubuntu..????

---

### Post by sidzen on 2010-05-30
Call me whatever you wish, but if another Windows system was used to format, I would not trust it to do a thorough job;  also, I have seen where simply using gparted or PartedMagic without first wiping the HD clean results in a failed install -- especially when Windows was the OS originally on the HD (Slackware distros sem to be particularly sensitive in this regard).  

dban can be obtained from:
[http://www.dban.org/download](http://www.dban.org/download)

Sometimes all one can do is to wipe the entire HD with zeros to get rid of all traces of viruses and other problems inherent with Windows before installing Linux.  This has been my experience, in any case, and I stand by it.

---

### Post by minhajmsm on 2010-05-30
kay sidzen... I'll take ya words nd will give it a go... already downloaded it also is written on to the CD... tonight ill try it n c... also got the 10.04LTS 2day..... I'll try..

   And Thanks a lot dear friend....

---

### Post by 3rdalbum on 2010-05-31
> **minhajmsm said:**
> Hi guys,, im new in here, and I have been using ubuntu for a certain period of time on a assembled system, and now I have a SAMSUNG system,,, when i try to install ubuntu - when i select install or try without..... all I get is a black screen and a cursor blinking..!!!!! :confused: ... so far Ive tried 8.10 DVD, 9.04 CD, 9.10 CD ,,,, all are same.... pls anyone help me.....

My god, people are suggesting all sorts of destructive courses of action without checking the basics.

Sometimes you need to apply special parameters to the kernel in order to get it to boot on some systems. When you start Ubuntu and it gives you the Ubuntu logo and two little symbols at teh bottom of the screen (keyboard and a man with many arms), press the space bar.

You'll be taken to a menu where you can choose various options for starting Ubuntu. If you press, I think, F9, it brings up a little popup menu with the options:

acpi=off
noapic
nolapic

Put a little cross next to those three options, press Escape to close the popup menu and press Enter to boot. Hopefully this should work.

---

### Post by minhajmsm on 2010-05-31
ahhhhh.. now im getting confused n scared..... :confused:

---

### Post by minhajmsm on 2010-05-31
Hey guys.. i did nothing .. Installed the 10.04LTS with out a problem..... n it rox... every hardware works perfectly.... only installed NVIDIA driver also downloaded automatically..... :guitar: 


Thanks a lot guys.....

---

