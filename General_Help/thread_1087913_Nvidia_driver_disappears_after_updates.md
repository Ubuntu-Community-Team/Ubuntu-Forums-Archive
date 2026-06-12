---
title: "Nvidia driver disappears after updates"
date: 2009-03-05
forum: General Help
---

### Post by xyloeye on 2009-03-05
I understand that Nvidia drivers are a pain in Ubuntu, but now that I finally have the routine down for installation, I'm still mystified that nearly every time I update, the driver disappears and I'm back to low graphics mode and another reinstall of the driver. What would cause this?

---

### Post by DeMus on 2009-03-05
> **xyloeye said:**
> I understand that Nvidia drivers are a pain in Ubuntu, but now that I finally have the routine down for installation, I'm still mystified that nearly every time I update, the driver disappears and I'm back to low graphics mode and another reinstall of the driver. What would cause this?

This is not an answer to your question, since I also find installing the video driver a pain in the b*tt. I was just wondering how you do install the nVidia driver. I found a way myself:
[http://ubuntuforums.org/showthread.php?t=1054842]()
but maybe you have a nicer and better way.

Thanks.

---

### Post by avtolle on 2009-03-05
> **xyloeye said:**
> I understand that Nvidia drivers are a pain in Ubuntu, but now that I finally have the routine down for installation, I'm still mystified that nearly every time I update, the driver disappears and I'm back to low graphics mode and another reinstall of the driver. What would cause this?
Since you are manually installing the drivers, each kernel update results in the need to reinstall them. I noticed that the drivers I installed through the hardware drivers application in 8.10 (177) don't break when new kernels come through; watching the process yesterday, I noted there was something called DKMS that checked for the presence of the driver, and then made sure it was installed correctly within the new kernel. Perhaps someone with more knowledge than I can comment about whether this may be installed from the package manager, and if so, whether once installed it can "transfer" (for lack of a better term) the nvidia driver manually installed on kernel x to kernel x+1.

---

### Post by 4Orbs on 2009-03-05
[Here is a nice little How-To]("http://ubuntuforums.org/showpost.php?p=5227704&postcount=1") for installing a script that will automatically update a manually installed nvidia driver whenever a kernel update occurs.

---

### Post by HH60Gunner on 2009-03-05
I'm fairly new to linux but this is how I got my Nvidia driver to work.

1.  Go to console

2.  Type:  Sudo apt-get install Nvidia*

3.  From there it will show you a list of possible combinations

4.  Look at the one that says nvidia binary driver 180, or 177 if you so chhoose.

5.  Then again type: sudo apt-get install (whichever driver you liked from the list.)

After doing that my driver was installed correctly, I restarted my machine and all has been well since.

---

### Post by avrilrox on 2009-03-05
Install Envy and install the drivers from there. Good luck!

---

### Post by stchman on 2009-03-05
> **xyloeye said:**
> I understand that Nvidia drivers are a pain in Ubuntu, but now that I finally have the routine down for installation, I'm still mystified that nearly every time I update, the driver disappears and I'm back to low graphics mode and another reinstall of the driver. What would cause this?

Activating the restricted driver is as easy as it gets.

---

### Post by Therion on 2009-03-05
> **xyloeye said:**
> I understand that Nvidia drivers are a pain in Ubuntu, but now that I finally have the routine down for installation, I'm still mystified that nearly every time I update, the driver disappears and I'm back to low graphics mode and another reinstall of the driver. What would cause this?
What "routine"?  System/Administration/Driver Manager (or I guess it's Hardware Manager in Intrepid) and click on the driver you want from the list of available choices.

Easy-peasy, lemon squeezy and no problems with kernel updates.

---

### Post by xyloeye on 2009-03-05
Thanks for all the replies. Demus asked how I install Nvidia drivers:
   Use synaptic to make sure no other remnants of Nvidia drivers remain
   Sudo rm /tmp/.X0-lock
   Sudo sh and drag or type location of driver in terminal.
   It will rebuild the kernal then compile
   After reboot, the driver will either work as is or you have to manually 
   reconfigure xorg.conf for HorizSync, VertRefresh and Modes i.e     
   1024x768_60 to make whatever monitor you have happy. (I'm using an old
   CRT that doesn't like the default values.

I have tried most other methods to install these drivers (believe me), including Envy without success. Envy likes to say everything is updated and installed, but I find the same old issues after reboot.

Thanks again for all the help. I didn't realize the update(s) were rebuilding the kernal each time. That helps my slooow journey to understanding.

---

