---
title: "Gnome with kubuntu problems"
date: 2016-02-27
forum: Desktop Environments
---

### Post by vaibhav_chutani on 2016-02-27
Hello, I am new to ubuntu, so I was trying out various things that can be done with ubuntu. I installed Gnome desktop environment with Appgrid. I used it for a while and wanted to try KDE. I installed Kubuntu with the Appgrid. The installation was not succesful. I started experiencing problems. To be very frank I did not completely read the error messages I got. I got a lot of pop ups to report the errors to the developers. I was redirected to web pages containing confirmed bugs.

I did not know what to do, so as a naive user I restarted my system.After the restart, I get black screen every time. I do not get any login screen, I see kubuntu logo then a black screen with mouse pointer. I have tried to wait but nothing happens and I am stuck at the black screen. Although other options such as changing brightness seems to be working on that black screen. I also used to see a default pink background on my grub menu, but after getting this black screen I see black grub background.

I tried fiddling with a few options. When I boot into advance options of ubuntu from the grub menu, The generic upstart 30.0 option boots me into ubuntu with unity background. In generic upstart I tried uninstalling kubuntu with different set of commands completely ( aptitude etc) but nothing seems to work. When i try to boot into the default ubuntu option again the same black screen happens. Please help me fix this. Thank you for all the help.

---

### Post by vasa1 on 2016-02-27
> **vaibhav_chutani said:**
> Hello, I am new to ubuntu, ... I installed Kubuntu with the Appgrid. ...
I did not know what to do, so as a naive user ...

I'm assuming you're also new to Linux. Is that correct? If so, I suggest you stay with one desktop environment and do whatever testing you want in a virtual machine. Some desktop environments don't play well together when installed on the same system.

I also think it's better if you let people know your computer's hardware capabilities (CPU, GPU, RAM).

Rather than trying to untangle stuff, I'd suggest a clean reinstallation of whichever flavor you want iff your computer is up to the task. Some distros don't run well on older hardware; some can't handle certain graphic cards; some may not support your wifi card out-of-the-box ...

---

### Post by vaibhav_chutani on 2016-02-27
Yes, you are correct. I am new to linux. I did not know that. 
I have a pavillion g6 1a75dx. I am attaching a screenshot containing all the hardware details. Please help me untangle the stuff because having to reinstall a fresh copy with all the programs i have already installed as well as the repositories already added would be a very big task. I am grateful for all you help. 

```

Harware -
Microprocessor 
2.53GHz Intel Core i3-380M Processor
Microprocessor Cache
3MB L3 Cache
Memory
4GB DDR3 System Memory (2 DIMM)
Memory Max
Maximum supported = 8GB
Video Graphics
Intel HD Graphics
Video Memory
Up to 1696MB
Display
15.6" diagonal High-Definition HP BrightView LED Display (1366 x 768)
Network Card
Integrated 10/100 Ethernet LAN
Wireless Connectivity
802.11b/g/n WLAN

External Ports
Digital Media Card Reader for Secure Digital and Multimedia cards
3 Universal Serial Bus (USB) 2.0
1 HDMI
1 VGA (15-pin)
1 RJ -45 (LAN)
1 Headphone-out
1 Microphone-in

```

---

### Post by vasa1 on 2016-02-27
> **vaibhav_chutani said:**
> Yes, you are correct. I am new to linux. I did not know that. 
I have a pavillion g6 1a75dx. I am attaching a screenshot containing all the hardware details. Please help me untangle the stuff because having to reinstall a fresh copy with all the programs i have already installed as well as the repositories already added would be a very big task. I am grateful for all you help. 
...
First, your system should be able to handle any Linux distro, AFAICT.

Second, for future use, please use the [CODE] tags to provide input such as specs as well as the command you used to generate the output.

If you don't have bandwidth limitations, I still feel doing a clean install is the way to go rather than trying to troubleshoot what went wrong (although it is certainly possible).

Then, once you have a vanilla system going, take things one step at a time :)

BTW, are you dual-booting with any other OS?

---

### Post by vaibhav_chutani on 2016-02-27
Yes, bandwidth is the biggest limitation. Yes i am also dual-booting with windows 10. I'll remember to use the [CODE] tags next time.

---

### Post by vaibhav_chutani on 2016-02-27
So what I did was, installed system package manager and searched for "KDE" and "Kubuntu" and uninstalled any packages that contained these keywords. Almost around 400 packages were uninstalled and 700MBs of packages. Now I have my doubts that I might have uninstalled important packages, that could be required for proper functioning of ubuntu. What I wanna know is there any command that I can run which can check all the things( I dont know packages, file system, things that are necessary) required for smooth functioning. Thanks.

---

### Post by vaibhav_chutani on 2016-02-27
Also I found out that when I boot in advanced option of the grub menu, I see 3 recovery options(30.0 generic, 27 something and 16 something). I tried running the 30.0 option which I was able to run before removing the packages but it does not, it gets stuck at the starting point. Same with 27 something, gets stuck at the same point. But 16 something works fine. Please help me with this problem.

---

### Post by SeijiSensei on 2016-02-27
While it's possible to install the meta-package "kubuntu-desktop" on top of a vanilla Ubuntu system, I have never found that to work very well.  I suggest just installing [Kubuntu 14.04 directly from its CD]("http://cdimage.ubuntu.com/kubuntu/trusty/daily-live/current/").

---

