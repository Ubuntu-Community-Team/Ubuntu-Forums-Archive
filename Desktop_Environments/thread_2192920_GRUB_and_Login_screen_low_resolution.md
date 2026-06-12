---
title: "GRUB and Login screen low resolution"
date: 2013-12-10
forum: Desktop Environments
---

### Post by pkdev on 2013-12-10
Hi i have a problem with my GRUB and login screen. Resolution is very low, but when i log in  my resolution is ok(1920x1080).
What is going on?

---

### Post by Confused Computer User on 2013-12-10
GRUB by default has a low resolution. That is normal. The log in screen should have the same resolution as your desktop.

Please post your distro information.
i.e. ubuntu 12.04 or Kubuntu 13.10

---

### Post by pkdev on 2013-12-10
ok thanks for the reply. Im using ubuntu 13.10 
Ubuntu icon is very big when its loading. its not looking like there [http://www.linoob.com/wp-content/uploads/2011/04/Ubuntu-Bootscreen.png](http://www.linoob.com/wp-content/uploads/2011/04/Ubuntu-Bootscreen.png)
 Login screen for 1 sec resolution is 1920x1080 but in a moment is changing to 1366x768.

---

### Post by Confused Computer User on 2013-12-10
hmh... sounds like the video card to me.
What I mean is that in my experience when using the intel (on board) graphics card, things run pretty smoothly.
But, if you have ATI or NVIDIA things start to be funky when you transition from Grub to the normal session.
Can you please confirm if you have a video card and if so which one.

---

### Post by pkdev on 2013-12-10
i think u are right. Ive installed nvidia drivers to my GeForce GT640 today

---

### Post by Confused Computer User on 2013-12-10
Ok... so then you can follow the instructions below in order to try to fix it. Keep in mind that I only tried this once, and that was years ago. I have since stoped using NVIDIA or any other videocard except for Intel. More work than what it's worth from my perspective.

> After installing Nvidia drivers in Ubuntu you lose that beautiful Plymouth boot screen. Here's how to fix that:

    In Grub press C and enter vbeinfo. It will show supported resolutions
    Boot Ubuntu and in terminal write sudo gedit /etc/default/grub
    After line #GRUB_GFXMODE=640x480 write GRUB_GFXPAYLOAD_LINUX=1680x1050x32 (here your supported resolution)
    Next in terminal: echo "FRAMEBUFFER=y" | sudo tee -a /etc/initramfs-tools/conf.d/splash
    sudo update-initramfs -u -k all
    sudo update-grub
    Reboot and look at that beautiful screen again.

P.S.: If this didn't work for you, try this method.
Taken from: [Fix Ubuntu Boot Screen (Plymouth) After Installing Nvidia Drivers]("http://randomandlinux.blogspot.ca/2013/05/fix-ubuntu-boot-screen-after-installing.html")

The second method that is mentioned at the end of the above quote is:
> 
    sudo apt-get install v86d hwinfo
    sudo hwinfo --framebuffer
    Choose highest resolution
    sudo gedit /etc/default/grub
    Change line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to look like this GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"
    Uncomment and change line GRUB_GFXMODE=1280x1024-24
    sudo gedit /etc/initramfs-tools/modules
    At end of file add line uvesafb mode_option=1280x1024-24 mtrr=3 scroll=ywrap
    echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
    sudo update-grub
    sudo update-initramfs -u
    Restart computer.
 
Taken from: [(Another Method) Fix Ubuntu Boot Screen (Plymouth) After Installing Nvidia Drivers]("http://randomandlinux.blogspot.ca/2013/06/fix-ubuntu-1304-boot-screen-plymouth.html")
Let me know if it helped, and if yes, mark the thread as solved.

---

### Post by pkdev on 2013-12-10
I used first method. And boot screen is looking good now, but login screen still has low resolution, i guess its 1366x768.

---

### Post by Confused Computer User on 2013-12-10
> **pkdev said:**
> I used first method. And boot screen is looking good now, but login screen still has low resolution, i guess its 1366x768.

Hmh, for some reason I think you pm-ed me your post.

That aside, the next bit you should really, really read and think about it carefully.
> Unfortunately this just breaks things in Ubuntu 13.04. Probably because they have been making some massive changes to the OS. –  pthurmond Sep 23 at 15:24
> Also doesn't work with Ubuntu 13.10 + NVIDIA driver 319: The script is executed but the resolution doesn't change - probably because the NVIDIA driver overrides it. –  speakr Nov 5 at 8:12 

The above quotes are taken from: [Wrong Login Screen Resolution]("http://askubuntu.com/questions/73804/wrong-login-screen-resolution")
The link leads to an askUbuntu page that details how to fix the resolution issue.

Use at your own risk.

I couldn't find any other link that would be more useful.

P.S.
Possibly unrelated, but, why did you choose to use Ubuntu 13.10?
I ask because I tended to install the latest and greatest when I first started using Linux and that led to numerous days wasted trying to fix issues that would eventually get sorted out through updates and be replaced by other time consuming, "joy" invoking, hair loss causing, bugs.
If you plan on using the computer as a work station, then you stand to benefit more from the LTS release (i.e. 12.04).
Feel free to disregard this if your not concerned.

---

