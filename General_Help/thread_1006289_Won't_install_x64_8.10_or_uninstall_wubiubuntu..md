---
title: "Won't install x64 8.10 or uninstall wubi/ubuntu."
date: 2008-12-09
forum: General Help
---

### Post by r00t_decision on 2008-12-09
I am trying to install ubuntu for the first time and I used wubi.
Installed 8.10 x64 on a partitioned **empty** hard drive and then I go this [error]("http://ge.ubuntuforums.com/showthread.php?t=963892&page=8").  I had to shut off my pc by turning off the power because it was hanging, and tried twice to reinstall.
Then I wanted to uninstall wubi/ubuntu in Vista x64 in uninstall programs and it won't uninstall.

1. How do you uninstall ubuntu/wubi in Vista
2. Will install and shutting off my pc, affect my hard drive or my 2nd partitioned C: , my ubuntu was installed in empty D:
3. Why can't I install 8.10 x64 ubuntu?

I'm downloading 8.04 ubuntu x64, to try it again. Is there a difference between 8.04 and 8.10, I really want to install the latest version because it looks so good.

---

### Post by razvanescu on 2008-12-09
First of all,you should install wubi on the same partition as Vista. You say you've got "Aperture beyond 4GB" error after installing ?

If you cannot uninstall it, and you say it was installed on an empty hard drive, try formatting the hdd and remove all information about wubi from the vista registry and take a look to Vista bootloader (with EasyBCD) to be shure nothing's left there. 
If you have an empty hard drive, why don't you install Ubuntu on it as a single OS ? and if you like Ubuntu, modify Vista bootloader to enable dual boot.
Good luck!

---

### Post by r00t_decision on 2008-12-09
> First of all,you should install wubi on the same partition as Vista. You say you've got "Aperture beyond 4GB" error after installing ?
Yeah, I read that now. I didn't expect that though, didn't read the install faq before wubi.  Yes I get "aperture beyond 4gb" error after installing.
> 
If you cannot uninstall it, and you say it was installed on an empty hard drive, try formatting the hdd and remove all information about wubi from** the vista registry and take a look to Vista bootloader (with EasyBCD) to be shure nothing's left there. **
I only have one hd. It's partitioned into two areas, the D: being empty. I can't reformat the hard drive, or can I, without reformatting the C:? (it's been a while since I did this sort of stuff)

Can you be more specific in direction with the bold, thanks.
> 
If you have an empty hard drive, why don't you install Ubuntu on it as a single OS ? and if you like Ubuntu, modify Vista bootloader to enable dual boot.

I can't uninstall Vista, because this is not my main pc. I only have one hd with Vista on it. If I had an empyt hard drive, would be easier. :)

---

### Post by razvanescu on 2008-12-09
> 
Installed 8.10 x64 on a partitioned empty hard drive and then I go this error.
I thought you have an empty hard drive from what you said here.
About the error...I have no idea! Keep watching the thread, maybe it will be solved somehow. You can format a partition, without formatting the entire hdd (from my computer, just right click on the partition you want to format, and choose format - is that simple)
Since Vista has no boot.ini file, you can modify the bootloader (the file that contain information about OS installed on a system and the order to boot them) by using this tool - EasyBCD (download link and how to here: [http://www.softpedia.com/get/System/OS-Enhancements/EasyBCD.shtml]("http://www.softpedia.com/get/System/OS-Enhancements/EasyBCD.shtml")). You should ensure there's no entry left about ubuntu in the bootloader. 
You can however have a dualboot system, even with a single hdd (see here a step-by-step tutorial with screenshots on how to do it: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm"))

cheers!


PS - The only difference is that you don't have to shrink the C: partition, if you want to install Ubuntu on D:

---

### Post by r00t_decision on 2008-12-09
Thanks, if I have any more questions I'll be sure to ask.

I used Vista restore mode and removed the wubi installer. Didn't want to go through registry and all the other stuff. :)
I'm also reformatting the D drive now.

Wubi installer initiates now again, before it did not because of the install error probably.

---

### Post by r00t_decision on 2008-12-09
Hi, another questions.

On bootup, I get the option to install Vista and Ubuntu. How do you remove this option/screen and bring it to normal vista bootup. ?

---

### Post by r00t_decision on 2008-12-10
Hi may I get some help with the above? Do I have to remove registry keys from Vista and Easy BCD stuff? If so how do you do that? I have EasyBCD installed, just don't want to destroy anything. :lolflag:

---

### Post by razvanescu on 2008-12-10
On bootup you got two options: to **start** ubuntu or vista. And that's the way it should be. You have to choose between the 2 OS installed on your system, and you shouldn't remove anything. If you remove the Vista entry from the bootloader with EasyBCD, you won't be able to start your computer under Vista. Just leave it like that

---

### Post by r00t_decision on 2008-12-10
Let me establish that I don't have ubuntu installed remember, I erased it from my D:.

-I formatted my D partitioned drive
- I did a system restore to remove ubuntu from the "uninstall"

The choice of options should not be there unless, I have to remove futher things. I just want to use Vista, and I will install ubuntu at a later date.

How can I remove that option of Vista/ubuntu at the boot up, when I don't have ubuntu installed.

---

### Post by razvanescu on 2008-12-10
> How can I remove that option of Vista/ubuntu at the boot up, when I don't have ubuntu installed.
by using EasyBCD - a bootloader editor for Vista

---

