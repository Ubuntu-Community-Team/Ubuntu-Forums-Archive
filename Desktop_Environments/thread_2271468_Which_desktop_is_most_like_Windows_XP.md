---
title: "Which desktop is most like Windows XP?"
date: 2015-03-30
forum: Desktop Environments
---

### Post by jack127 on 2015-03-30
I recently installed ubunor to linux on a Acer Aspire One notebook using the kubuntu-14.10-desktop-i386.iso image.  For a brief time I had a desktop with a starter bar along the lower edge of the screen and I think it was called the KDE starter or something like that.  In the course of messing around with it a little I lost that and the starter changed appearance and moved to the top of the screen.  And then the install was lost when I had a hard drive problem.  

I am about to install again and want to know what desktop it is that I might have had that was much like XP.  And maybe where I can get it.  

And if there is a place that shows the various desktops I might want to consider, a link to that would be helpful.  

Thanks,  

Jack

---

### Post by buzzingrobot on 2015-03-30
A number of interfaces, and the Ubuntu variants that use them, are based on the same panel-and-menu design used in Windows. KDE is used in Kubuntu, MATE is used in Ubuntu Mate, XFCE is used in Xubuntu, and LXDE is used in Lubuntu.  Each variant has its own site where you can get an idea of how it looks and download a Live Image to boot and test. (Using Google's image search will turn up thousands of desktop images for each.)

Zorin OS is a derivative distribution based on Ubuntu that makes a specific effort to include an interface familiar to XP users. Google will find the site.

---

### Post by oldfred on 2015-03-30
This comparison is of now obsolete version, but the screens are essentially still the same.
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_raring_desktops1&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_raring_desktops1&num=1)

       Comparison of desktop environments - diffences in software
[https://wiki.archlinux.org/index.php/Desktop_Environment](https://wiki.archlinux.org/index.php/Desktop_Environment)
[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)

I have used another standard Ubuntu that is a bit more lightweight called either fallback or gnome-panel. It uses top & bottom panels and is like the old gnome2 standard Ubuntu before Unity.
      
 Gnome fallback Compiz vs Metacity, what's the diff?
[http://ubuntuforums.org/showthread.php?t=2250933](http://ubuntuforums.org/showthread.php?t=2250933)

 Classic, fallback, flash back explanation -  by kanasnoob 
[http://ubuntuforums.org/showthread.php?t=2185161](http://ubuntuforums.org/showthread.php?t=2185161)
How to choose Display manager sessions -  by kanasnoob 
[http://ubuntuforums.org/showthread.php?t=2184682&p=12929682#post12929682](http://ubuntuforums.org/showthread.php?t=2184682&p=12929682#post12929682)

Best to have one standard working install and use another install as test or for experimentation. Then if you find a better one you can switch or update main working install.

---

### Post by jack127 on 2015-03-31
Thanks for the replies and help guys!  

I'm going to install kubuntu-14.04.2-desktop-i386.iso using the Linux Live USB device to get started again

A couple of questions...

"..Best to have one standard working install and use another install as  test or for experimentation. Then if you find a better one you can  switch or update main working install..." 

When you install a second version of linux, will it use the partitions set up for the first install?  I will have a 15 GB root partition and 130 GB /home partition so there willl be enough space for the second install if it can be used.  

Is it easy to selectively uninstall the second version and leave the first intact?  

IThis will be on a netbook with XP already installed.  s there a way to make the grub2 multiple boot setup be located only on the linux partition?  So that if I want to start over I can do that just deleting the linux partition? 

 I did that once before and then had to use the fixmbr option from the XP install CD to get the no longer working grub boot to go XP.  

Jack

---

### Post by oldfred on 2015-03-31
I have a larger hard drive and just create additional / (root) partitions of 20 or 25GB. I do keep /home inside / but then have separate data partition. Since many user settings are in /home often best not to share them as settings may conflict or you may change something in one system that you do not want changed in the other system.

You also have to manage which install's grub is in charge or in MBR. I have several drives and working install booted from sdd, and all test installs just installed grub to sda. So most recent test would always boot all newer installs. 
You can do the same thing by forcing grub to install to partition boot sector which otherwise is not normally recommended. But if you later want to make that a working install you must reinstall its grub to MBR before reconfiguring anything else.

---

### Post by Kirkx on 2015-04-02
Have a look at the following distros: ChaletOS, Zorin, Q4OS:

[https://sites.google.com/site/chaletoslinux/home](https://sites.google.com/site/chaletoslinux/home)

[http://zorin-os.com/](http://zorin-os.com/)

[http://q4os.org/index.html](http://q4os.org/index.html)

---

### Post by Siddhartha_Kashyap on 2015-04-04
definitely Zorin OS 

[img]http://distrowatch.com/images/cgfjoewdlbc/zorin.png[/img]

---

### Post by Kirkx on 2015-04-06
You don't really need to install Zorin or ChaletOS. You can just get Windows-like icons and themes and install them in Ubuntu. Here are a few examples.

1) Package xfwm4-themes (available in Synaptic). Look for Redmond and RedmondXP themes.

2) YlmfOS XP Theme Pack from Noobs Lab:** [http://www.noobslab.com/2014/05/recall-old-memories-of-xp-with-ylmfos.html](http://www.noobslab.com/2014/05/recall-old-memories-of-xp-with-ylmfos.html)**

3) Windows 98 look: [https://github.com/paldepind/Gtk98Icons](https://github.com/paldepind/Gtk98Icons)

---

