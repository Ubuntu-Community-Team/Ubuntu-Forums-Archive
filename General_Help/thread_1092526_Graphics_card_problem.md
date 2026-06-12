---
title: "Graphics card problem"
date: 2009-03-10
forum: General Help
---

### Post by Ibrahim mufeed on 2009-03-10
Hi everyone,

After I installed the latest Ubuntu version 8.10, the OS automatically found a suitable driver for my ATI VGA card, and I download it and install it. and everything goes well, and I notice a BIG deference it was great, like never been before with Ubuntu 8.04 .

The problem is that almost always when I turn on my PC normally, and after the preparation and completing the orange line. it displays a black screen and did not show the login window I was waiting for .

So, I started to use the the "Recovery" options from the grub menu, and then select "Resume normal..", and other times it did not work even so I choose "Repair broken packages" and then "Resume normal...".

What I notice is that when I "Deactivate" my ATI driver the PC works fine. but the screen looks bigger without "Activating" the driver -You know-.
 
after this, one member here told me to get the latest driver update with:
```

wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-9.2-x86.x86_64.run

```

and 
```
sudo sh ati-driver-installer-9.2-x86.x86_64.run
```
then configure X with the new driver:
```
sudo aticonfig --initial -f
```

I did all that and everything goes right, After I fix it and everything works just fine, from time to time I face a new problem.

That's sometimes when I turn on my PC, after filling the ORANGE progress bar, and instead of seeing the login screen, it shows a black one with the word UBUNTU on the top of the page, like this:

Ubuntu Ubuntu Ubuntu Ubuntu
====== ====== ====== ======

and fuzzy.

the "=======" represent progress bars 'not working for sure'.

---

### Post by Nano_ext3 on 2009-03-10
Hi,

I suggest not even messing with that driver.  ATI really does dislike Linux, ask many here and youll get the same answer.  You should use the widely acclaimed EnvyNG app. 

Installing EnvyNG , which is a fantastic program to install your ATI / or Nvidia driver automatically, is easy. This will also, in addition to the graphics driver, a repository addition , so your normal system updates will include the latest driver , when the EnvyNG developer decides to code the latest stable driver. The developed tends not to code , or push the Beta drivers, which are the latest on nvidia's webside (do not know about ATI)

Install EnvyNG by doing:

Gnome : sudo apt-get install envyng-gtk
KDE : sudo apt-get install envyng-qt

This can be also done via Synaptics Package manager under,System > Administration > Synaptics.  From here check your /etc/X11/xorg.conf file and make sure your driver, under device I believe a sub-entry for your video card should have a driver such as "ati" or "nvidia."



Hope this helps,

Let me know if you need anything else.


Cheers!

-Nano
__________________

---

### Post by CrusaderAD on 2009-03-10
I can speak for envyng... IT WORKS GREAT.

---

### Post by chemamar on 2009-03-10
> **Nano_ext3 said:**
> Hi,

I suggest not even messing with that driver.  ATI really does dislike Linux, ask many here and youll get the same answer.  You should use the widely acclaimed EnvyNG app. 

Installing EnvyNG , which is a fantastic program to install your ATI / or Nvidia driver automatically, is easy. This will also, in addition to the graphics driver, a repository addition , so your normal system updates will include the latest driver , when the EnvyNG developer decides to code the latest stable driver. The developed tends not to code , or push the Beta drivers, which are the latest on nvidia's webside (do not know about ATI)

Install EnvyNG by doing:

Gnome : sudo apt-get install envyng-gtk
KDE : sudo apt-get install envyng-qt

This can be also done via Synaptics Package manager under,System > Administration > Synaptics.  From here check your /etc/X11/xorg.conf file and make sure your driver, under device I believe a sub-entry for your video card should have a driver such as "ati" or "nvidia."



Hope this helps,

Let me know if you need anything else.


Cheers!

-Nano
__________________
But what does Envy install? The open source driver?

Thanks.

---

### Post by Ibrahim mufeed on 2009-03-10
Hi,

I have done the 
```
sudo apt-get install envyng-gtk
 
```command you told me about, but then I do not understand what you said about:
> 
From here check your /etc/X11/xorg.conf file and make sure your driver, under device I believe a sub-entry for your video card should have a driver such as "ati" or "nvidia."


would you explain if I have any other thing to do with "xorg.config"?

Thanks,

---

### Post by CrusaderAD on 2009-03-12
I didn't have to edit anything in the xorg.config file. I just installed envyng and it worked.

---

### Post by Yellow Pasque on 2009-03-12
Some ATI owners report that Envy doesn't work for them, but I see a lot of praise for this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

---

