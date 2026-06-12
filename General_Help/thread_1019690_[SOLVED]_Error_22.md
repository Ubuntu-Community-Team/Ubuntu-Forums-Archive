---
title: "[SOLVED] Error 22"
date: 2008-12-23
forum: General Help
---

### Post by ChrisUb.Linux on 2008-12-23
Hello.
A friend of mine used to have Windows Vista and Ub Linux 8.04 in the same hard disk (dual-boot). It seems that he made some changes and now when he turns on his laptop the Error 22 appears (it has something to do with GRUB I think...). So..he just wants to get Vista working without formatting the whole disk (and lose his data). Can we access Vista now in any way?
Please help if you can. 
Cheers.

---

### Post by caljohnsmith on 2008-12-23
From the Ubuntu Live CD you should be able to mount the Vista partition if you go to the Places menu on the desktop. Does your friend just want to be able to boot into Vista at this point, or does he want to fix Ubuntu? If he wants a "quick fix" in order to boot into Vista, he could open a terminal from the Ubuntu CD (Applications > Accessories > Terminal) and do:
```
sudo lilo -M  /dev/sda mbr
```
And then he should be able to boot directly into Vista assuming there are not issues with Vista, and also assuming the boot flag is set on the Vista partition. If your friend would like help diagnosing his Grub problem though, how about having him post the output of:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; if he can post those results, that will help clarify his setup and hopefully what his problem might be.

---

### Post by redilyn on 2008-12-23
Why would he ever want to give up on Ubuntu in favor of vista.

Regardless, Here is how to fix grub.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by gettinoriginal on 2008-12-23
Hope these help:  :P  Good Luck

[http://ubuntuforums.org/showthread.php?t=206262](http://ubuntuforums.org/showthread.php?t=206262)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by ChrisUb.Linux on 2008-12-23
Thanks guys. Amazingly fast replies! Will try these things out. Ill keep you posted!

---

### Post by ChrisUb.Linux on 2008-12-23
The problem persists. Even if we install Ubuntu again, we get the same error.
When we try to run the recovery mode from Vista and type "fixmbr", Vista does not even recognizes the "fixmbr" command...

---

### Post by ChrisUb.Linux on 2008-12-24
Managed to fix it thanks to Vista's recovery disc. Used the "fixmbr" command correctly this time :P. Seems that Bill had the idea of changing the command of XP in Vista  :confused:.

Couldnt have made it without your help guys thanks :popcorn:

---

