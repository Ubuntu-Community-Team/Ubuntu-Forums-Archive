---
title: "Ubuntu 10.04 RaLink RT2860 does not connect"
date: 2010-05-01
forum: Florida Team - US
---

### Post by aliencure on 2010-05-01
:confused: Hello guys. Been a long time since I have been here. My wireless network card, RaLink RT2860, does not connect to the router when I load Ubuntu, with Linux 2.6.32-21-generic (GNU GRUB version 1.98-1ubuntu5). However when I load Ubuntu, with Linux 2.6.31-21-generic, wireless network works great with my only gripe being low graphics mode. Anyone have a suggestion or two on how to fix this? :confused:

:guitar:Thank you in advance. You rock!:guitar:

---

### Post by mlsquad on 2010-05-01
> **aliencure said:**
> :confused: Hello guys. Been a long time since I have been here. My wireless network card, RaLink RT2860, does not connect to the router when I load Ubuntu, with Linux 2.6.32-21-generic (GNU GRUB version 1.98-1ubuntu5). However when I load Ubuntu, with Linux 2.6.31-21-generic, wireless network works great with my only gripe being low graphics mode. Anyone have a suggestion or two on how to fix this? :confused:

:guitar:Thank you in advance. You rock!:guitar:

Is this on a laptop or different computer?  The 2.6.32 kernel is for Lucid, which I thought wasn't working for you.  If you are using Karmic then you should be on the 2.6.31 kernel.
There appears to already be a bug filed about this at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093)  It looks like there are temporary work arounds, and also a test kernel with the fix you could try installing.
Let us know how it works for you.

---

### Post by aliencure on 2010-05-01
I reinstalled Windows and Ubuntu 9.10 on a dual partition on my desktop. I then went into 9.10, installed updates, then restarted computer. Went back into 9.10 and upgraded to 10.04. Went straight to karmic version, googled how to reset X server settings for my NVIDIA 9500 GS, and did so in terminal. After restarting the computer, I was able to get into lucid.

---

### Post by aliencure on 2010-05-01
I really need help translating what these people are saying mlsquad. Patch I found also completely baffles me. When I looked at the bug link, it seemed to me these people are experts at programming so they have no problem understanding each other. I am not an expert on Ubuntu by any means, I am an extreme beginner. Am I supposed to type the lines from the patch into terminal? No offense to anyone I hope. I just do not understand some of the things they are saying.

---

### Post by ctbarker32 on 2010-05-01
> **aliencure said:**
> I am an extreme beginner. Am I supposed to type the lines from the patch into terminal? No offense to anyone I hope. I just do not understand some of the things they are saying.

Hi. I don't know if this will help but I have written up a tutorial specifically aimed at getting the Ralink RT2860 chipset working with wifi and WPA security. I think I have made it understandable for the novice. I am not a Linux expert by any means so that's where I'm coming from. Hope this helps.

[RT2860 and Ubuntu 10.04 wireless tutorial]("http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html")

-CB

---

### Post by aliencure on 2010-05-01
Thank you ctbarker32. I will try it out and let you know what happens.

---

### Post by aliencure on 2010-05-02
I am sorry ctbarker32. I got as far as step 6 and ran into a snag:

derek@derek-desktop:~$ sudo make
[sudo] password for derek: 
make: *** No targets specified and no makefile found.  Stop.
derek@derek-desktop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
derek@derek-desktop:~$ sudo ifconfig wlan0 down
derek@derek-desktop:~$ sudo rmmod rt2860sta
derek@derek-desktop:~$ sudo mv /lib/modules/2.6.32-21-generic/kernal/drivers/staging/rt2860/rt2860sta.ko rt2860sta.ko.dist
mv: cannot stat `/lib/modules/2.6.32-21-generic/kernal/drivers/staging/rt2860/rt2860sta.ko': No such file or directory

Stopped at this point.

---

### Post by dpsousa on 2010-05-02
aliencure, you have to open the terminal in the extracted driver folder and run those commands from there.

---

### Post by aliencure on 2010-05-02
How do you open the terminal in the extracted driver folder?

---

### Post by Tidder on 2010-05-02
> **aliencure said:**
> How do you open the terminal in the extracted driver folder?

From the terminal, you use the 'cd' command.  If you downloaded to your 'Downloads' folder and extracted it there, it will be similar to this:

1. Open Terminal
2. type in 'cd Downloads' and hit enter (without the quotes)
3. type in 'cd ralink_driver_folder_name' and hit enter (without the quotes)

Of course replacing 'ralink_driver_folder_name' with the actual name of the folder.  On my machine it was 2010_01_29_RT2860_Linux_STA_v2.3.0.0

Then run your make commands from there.

---

### Post by Tidder on 2010-05-02
> **ctbarker32 said:**
> Hi. I don't know if this will help but I have written up a tutorial specifically aimed at getting the Ralink RT2860 chipset working with wifi and WPA security. I think I have made it understandable for the novice. I am not a Linux expert by any means so that's where I'm coming from. Hope this helps.

[RT2860 and Ubuntu 10.04 wireless tutorial]("http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html")

-CB

Thank you SO MUCH for the tutorial.  I knew I probably needed to build a new module, but building from the stock source left me even more broken than before.  I had no idea of the changes that needed made to the source.  This got me up and running perfectly on an MSI Wind U100.  Now the wife won't be mad that I upgraded her netbook. :)

---

### Post by dpsousa on 2010-05-02
> **ctbarker32 said:**
> Hi. I don't know if this will help but I have written up a tutorial specifically aimed at getting the Ralink RT2860 chipset working with wifi and WPA security. I think I have made it understandable for the novice. I am not a Linux expert by any means so that's where I'm coming from. Hope this helps.

[RT2860 and Ubuntu 10.04 wireless tutorial]("http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html")

-CB
Thank you!

From what I've read on the launchpad bug report that you linked, changing the *MIX_CIPHER_NOTUSE* line is not needed. Only the *HAS_WPA_SUPPLICANT* and *HAS_NATIVE_WPA_SUPPLICANT_SUPPORT* lines.

Ubuntu 10.04 64 bits + RT2860 here.

---

### Post by myoungf1 on 2010-05-02
> **ctbarker32 said:**
> Hi. I don't know if this will help but I have written up a tutorial specifically aimed at getting the Ralink RT2860 chipset working with wifi and WPA security. I think I have made it understandable for the novice. I am not a Linux expert by any means so that's where I'm coming from. Hope this helps.

[RT2860 and Ubuntu 10.04 wireless tutorial]("http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html")

-CB

Thanks for the tutorial.  I got Lucid installed today and had the same problem.  One thing to add make sure you have gcc installed for the commands make and make install will not work.  But went through the tutorial and everything works, except for speeds but with a reboot hopefully it works better.

---

### Post by aliencure on 2010-05-05
\\:D/ Thank you all! Got it working!! \\:D/

---

### Post by paradoxni on 2010-06-15
thanks for the guide! My ralink WAS working in 10.04 but was only showing 54M, I used ctbarker32's guide and am now showing up to 270M

My problem is when copying files. When idle the wireless shows 270M, but as soon as I copy a large file over the wireless network to my NAS which is wired to my router, the speed instantly drops to 108M and sometimes down to 54M, as soon as the file transfer completes the speed jumps back to 270M

---

### Post by JayOui on 2010-08-22
For those that stumble upon this, please note that the link in the guide no longer works. You need to download the latest package from the ralink site itself. I found that the standard unarchiver utility in ubuntu was unable to extract the latest source driver packageand I couldn't decompress it with bzip2 either. It worked in OSX so I just extracted it there and put it on the system with dropbox.

The guide works perfectly.

---

### Post by juddmeeks on 2010-08-25
I have a msi wind u100 and just last week upgraded from karmic to lucid and i had a little different problem with the wireless, mine will connect SOMETIMES (i.e. freshly restarted netgear router and netbook on AC power) but not regularly.  I tried to follow the guide posted above, but i can't seem to find the ./os/linux/config.mk or the ./common/cmm_wpa.c files that i need to edit.  anyone having the same issues or that can help??? please?

---

### Post by juddmeeks on 2010-08-27
> **juddmeeks said:**
> I have a msi wind u100 and just last week upgraded from karmic to lucid and i had a little different problem with the wireless, mine will connect SOMETIMES (i.e. freshly restarted netgear router and netbook on AC power) but not regularly.  I tried to follow the guide posted above, but i can't seem to find the ./os/linux/config.mk or the ./common/cmm_wpa.c files that i need to edit.  anyone having the same issues or that can help??? please?

please disregard my last post (quoted)...i'm an idiot and downloaded the wrong driver information from ralink...i'm all better now and my wind u100 is running at break-neck speeds

---

### Post by fletc900 on 2010-09-09
I'm using Ubuntu 10.04 on a 64 bit machine, and was having issues with the RaLink 2860 when I tried to connect to my WPA2 protected router.

I tried following the web blog posting mentioned above but the link to download the driver from the RaLink website was down, as someone had mentioned earlier. I've instead followed the workaround that was proposed for the Mandriva Linux distribution it works for ubuntu 10.04 too :p. This is also much quicker way fixing the issue (less steps involved):

[http://www.connect-utb.com/index.php?option=com_content&view=article&id=72:get-ralink-2860-working-in-linux&catid=34:linux&Itemid=64](http://www.connect-utb.com/index.php?option=com_content&view=article&id=72:get-ralink-2860-working-in-linux&catid=34:linux&Itemid=64)


Cheers

---

