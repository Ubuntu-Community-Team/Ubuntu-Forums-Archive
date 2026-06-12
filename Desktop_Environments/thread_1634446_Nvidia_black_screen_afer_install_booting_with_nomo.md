---
title: "Nvidia black screen afer install booting with nomodeset"
date: 2010-11-30
forum: Desktop Environments
---

### Post by bigfas on 2010-11-30
hey guys! 

running ubuntu 10.10, had to use nomodeset to successfully boot from cd into "Try ubuntu without installing" thing and install ubuntu.
Edited grub by adding nomodeset after quiet and splash in order to boot from hard disk, still booting that way as I'm writing.

The computer is an All In one Pc called ONETWOPWU44.
The graphic card is an NVIDIA g210m.

After booting into hard disk I installed the proprietary driver resulting in an alternate of white then gray then black then an Image with red blue and some other colours on the screen, not sure of the order but they came one after an other, right when the login form should appear, I am then able to login by tipping my password into the form and pressing enter, I now that cause I can hear the sound when the system loads but the above described situation continues.
I had the same result with an older nvdia driver it was 253 something, don't remember exactly.

Then I downloaded the 260.19.21 driver from nvdia website and installed it, with this one I only got a black screen.

I now have a fresh ubuntu 10.10 copy and would like to be guided in making this work.

How do I install the driver corectly or how do I enable nouveau 3d support?

---

### Post by bigfas on 2010-12-01
can't anybody help me?
maybe if I were to give some more details? I don't know what will be useful so pleas ask me if you need to know something to help me.

---

### Post by bigfas on 2010-12-03
up

---

### Post by bigfas on 2010-12-03
well I thought I will get some support from the "great" ubuntu community but seems I will just have to install windows 7 again.

---

### Post by moaoci on 2011-01-02
I just updated to Ubuntu 10.10 64bit (from 10.04 64bit) on AMD 64 Athlon processor and got the blank screen again.

lspci shows my card as : VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)

After each kernel upgrade, I reboot to a blank screen ( System prompt ) and no support for my graphic card. But the commands I used before are not working any more.

I found the solution here [http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html) and it worked.


Instructions:

Boot to safe graphic mode
Open a terminal and type this command to add the nVidia repository to the update manager:[INDENT]sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
[/INDENT]Then type these commands to refresh and install nVidia driver. The second command takes some time to execute...  Note that I didn't have to provide the graphics card number.  And the 2nd command is a single-line command
[INDENT] sudo apt-get update
sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
[/INDENT]Then reboot.

Let me know if it works for you

---

### Post by cmw on 2011-03-28
I have a fresh install of Ubuntu 10.10 (64-bit) and am using the Nvidia GeForce 8400 GS.  After installing the recommended Nvidia driver (the one offered by the "Restricted Drivers" prompt just after install) I rebooted into a black screen.  I hit CTRL+ALT+F1 to get a prompt to log in.  From the prompte  I followed moaoci's solution and it worked.  

Thanks.

---

### Post by lsiden on 2011-04-10
I tried this too but when I attempted "sudo apt-get install nvidia-current- ..." it ended with:

Failed to fetch [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/pool/main/n/nvidia-graphics-drivers/nvidia-current_270.29-0ubuntu~maverick~xup2_i386.deb](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/pool/main/n/nvidia-graphics-drivers/nvidia-current_270.29-0ubuntu~maverick~xup2_i386.deb) Hash Sum Mismatch

I also tried installing the proprietary driver from nvidia, but when I startx all I see is a mouse cursor on a blank screen, so I uninstalled.

FWIW, lspci shows

VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

---

### Post by syndacate2004 on 2011-05-03
Hello. I have the same problem: a pc with an integrated NVIDIA G210M and after installing the nvidia drivers, after the boot, appear on screen some colours: white, black, blue etc etc alternating...

How Can I solve this problem???? Please HELP!

---

### Post by BFG on 2011-05-07
> **moaoci said:**
> I just updated to Ubuntu 10.10 64bit (from 10.04 64bit) on AMD 64 Athlon processor and got the blank screen again.

lspci shows my card as : VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)

After each kernel upgrade, I reboot to a blank screen ( System prompt ) and no support for my graphic card. But the commands I used before are not working any more.

I found the solution here [http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html) and it worked.


Instructions:

Boot to safe graphic mode
Open a terminal and type this command to add the nVidia repository to the update manager:[INDENT]sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
[/INDENT]Then type these commands to refresh and install nVidia driver. The second command takes some time to execute...  Note that I didn't have to provide the graphics card number.  And the 2nd command is a single-line command
[INDENT] sudo apt-get update
sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
[/INDENT]Then reboot.

Let me know if it works for you

Unfortunately this solution does not work with G210M. Problems remain.  I've tried this and loads of other "solutions" and none of them are giving a result.:confused:

---

