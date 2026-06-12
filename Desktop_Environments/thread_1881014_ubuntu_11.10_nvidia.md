---
title: "ubuntu 11.10 nvidia"
date: 2011-11-14
forum: Desktop Environments
---

### Post by mr hippie on 2011-11-14
Hi,
I am a newbie trying to get multi monitor support, in the process I some how lost all monitor support.  When starting Ubuntu 11.10 the screen is now all garbled.  I can not log in.  Is there away to load a video driver in command line?

Thanks,

---

### Post by lolpenguin on 2011-11-15
When you start the computer, does it load LightDM or a tty
A tty would look like this:
```
Ubuntu tty1
Ubuntu login:
```

---

### Post by lolpenguin on 2011-11-15
If it loads a tty run
```
jockey-text
```
and uninstall and re-install any drivers.

If it loads a graphical session press Ctrl+Alt+F4 to open a tty.

---

### Post by randywilharm on 2011-11-15
> **mr hippie said:**
> Hi,
I am a newbie trying to get multi monitor support, in the process I some how lost all monitor support.  When starting Ubuntu 11.10 the screen is now all garbled.  I can not log in.  Is there away to load a video driver in command line?

Thanks,


You should download the latest NVIDIA driver here:
[URL="http://www.nvidia.com/Download/index.aspx?lang=en-us"]
http://www.nvidia.com/Download/index.aspx?lang=en-us[/URL]


You must install this as ROOT and you will have to turn
off gnome. The command is gdm stop or lightdm stop depending
on what you have for a desktop manager.

---

### Post by mr hippie on 2011-11-15
I just get a colored garbled screen.  Since this is a dual boot vista/ubuntu  I will have to shut down and see if I can get to the tty by pressing Ctrl+Alt+F4 

Thank you for your response as well.

---

### Post by mr hippie on 2011-11-15
So, I could not get to tty from my 11.10 install (dual boot).  But I tried it on my other hard-drive (SSD) running 11.04, that was from my old laptop and was not working on my pc.  The command 'jockey-text' unfroze it and now I am up an running.  

Just a note:  when I upgraded my laptop from 11.04 to 11.10 a few weeks later my ati video card died (I will be buying a new laptop day after thanksgiving).  Now that I have been messing around with 11.10 on my pc, before messed up my drivers, my second monitor went out/or the second video port on my graphic card died.  I am sure this is all coincidence.

---

### Post by flagbag on 2011-11-15
I am having same problem as poster, although I am not trying to get dual monito--I am just trying to use Ubuntu.
   My computer locks-up every time I try the UBUNTU Live CD (now DVD). I have ordered various versions over the past few years and none work, including the newest, 11.10. 
   I have suspected it has something to do with my Nvidia 7800 as I have seen some work arounds but all are old (2007-2009) and I can't get them to work with my Live CD. Here are screen shots, symptoms, and my hardware. 
   Only thing--while I am fairly computer-savvy, I am a total newbie to Ubuntu, so please phrase your help so I can go step-by-step if you would please be so helpful.
   Really appreciate help..... I would love to use Ubuntu and am frustrated for years...
   After restarting system w/ the Live DVD, I select 'English", then I select 'Try Ubuntu without installing on system.' 
   It seems to be loading fine, then locks up (no mouse or keyboard). There seems to be a graphic on the screen, "UBUNTU", but it is scrambled. 
[IMG]http://a.yfrog.com/img611/205/suw7.jpg[/IMG]
   My system is a homemade desktop, running WinXP (sorry for the bad language:)! CPU: AMD Athlon 64 3500+ with 3 gigRAM Moboard: MS-7125  video: Nvidia GeForce 7800GT. 
   Any ideas? Please??

---

### Post by weclark on 2011-11-16
I have a similar problem.

  I am still running Ubuntu 9.10 on a system with the Nvidia GeForce 7100 / nForce 630i (Asus P5N-EM HDMI) because on every update since I loose audio on the HDMI interface.

  When I boot from the 11.10 liveDVD it runs very slow and eventually hangs.

  I am looking for a way to run with the current Nvidia driver without having to install 11.10 just to find out I still have no audio.  Is there a way to add it to the liveDVD or run it?

---

### Post by weclark on 2012-01-28
I went ahead and installed Ubuntu 11.10 (both 32 and 64 bit versions).  I still cannot get HDMI audio to work.

EXCEPT: I did notice that speaker-test -c2 -twav works.:confused:

HELP!!!

---

### Post by grahammechanical on 2012-01-28
Here is a link to a sticky on the Installation & Upgrades section of the forum. It deals with some of these issues:

[http://ubuntuforums.org/showthread.php?t=1743535]("http://ubuntuforums.org/showthread.php?t=1743535")

It is a long thread. It takes some reading as the advice is comprehensive. It tries to cover many issues.

For those with problems running the live CD or getting to a log in screen, take a look at the third post and look at the second image. It shows how to change some boot options that may get the live CD running enough to get to a desktop from where you can install the drivers.

Regards.

---

