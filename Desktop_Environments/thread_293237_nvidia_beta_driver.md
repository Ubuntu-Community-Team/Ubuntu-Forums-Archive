---
title: "nvidia beta driver"
date: 2006-11-04
forum: Desktop Environments
---

### Post by johnny9794 on 2006-11-04
Hi all, i would like to install Beta Graphics Driver (NVIDIA) so i may install Beryl/AIGLX (Nvidia).

But i am having a problem, I read and followed the tut on "How to install Beta Graphics Driver (NVIDIA)" but when I went to install "libxorg-sched-yield-hack0" but got "Couldn't find package libxorg-sched-yield-hack0"

>  johnny@linux-box:~$ sudo apt-get install nvidia-glx libxorg-sched-yield-hack0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libxorg-sched-yield-hack0
johnny@linux-box:~$ sudo apt-get install libxorg-sched-yield-hack0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libxorg-sched-yield-hack0 

Could someone help me out plz or have any suggestions on what i shall do?

Here is my sources list file.

Thank You.

---

### Post by bluemax on 2006-11-04
I don't think you need the libxorg-sched-yield-hack0 package. I installed the beta driver without it, and everything works fine. Just comment out everything except amaranth's source in your sources.list (temporarily), and install nvidia-glx. You should be good to go then.

---

### Post by johnny9794 on 2006-11-04
> **bluemax said:**
> I don't think you need the libxorg-sched-yield-hack0 package. I installed the beta driver without it, and everything works fine. Just comment out everything except amaranth's source in your sources.list (temporarily), and install nvidia-glx. You should be good to go then.

Well if I or nobody needs it why would they have it in the tutoial???
[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29)

---

### Post by johnny9794 on 2006-11-04
Another thing is when I paste sudo nvidia-xconfig in the terminal.

> johnny@linux-box:~$ sudo nvidia-xconfig
sudo: nvidia-xconfig: command not found

I think that the command is not found because i do not have libxorg-sched-yield-hack0 installed.

When i was running ubuntu 6.06.1 i had nvidia-glx and nvidia-kernel-common
installed with XGL/compiz and everything worked fine.

Now that I am on edgy I would really like to get Beta Graphics Driver (NVIDIA) and Beryl/AIGLX (Nvidia) installed.

---

### Post by johnny9794 on 2006-11-05
Ok i got it all working "the bete driver " I would not suggest using 
the ubuntu starter guide on  How to install beta driver (Nvidia).

I would suggest using 

[http://forum.beryl-project.org/topic-5021-howto-beryl-aiglx-nvidia-drivers](http://forum.beryl-project.org/topic-5021-howto-beryl-aiglx-nvidia-drivers)

Works GREAT!!! :)

---

