---
title: "Beryl + Radeon 9200 SE"
date: 2007-06-14
forum: Desktop Effects &amp; Customization
---

### Post by ownedbyhleb on 2007-06-14
I have just installed Ubuntu on my old PC. I have 320MB of RAM, 1Ghz AMD Processor, and a Radeon 9200 SE (AGP) card. I would like to know how to install ATi drivers (if needed) and Beryl.

However, there is one problem. I dont have access to the Internet, so I'm fairly stuck.
Just wondering if there's any guide's avaible.

Thanks.

---

### Post by ajgreeny on 2007-06-14
I think you may be a bit low on ram for beryl to work very well, but here goes.

You will have to find a way of downloading beryl from the repos, I'm afraid, with any dependencies you may also need.  You can do it from another computer, even running the live CD, I think, if needed, and then copy the downloaded files to a CD or usb drive.  You can then install them on your own machine using **synaptic>File>Add downloaded packages** and navigating to the downloaded packages in the dialogue box that appears.  Your card should not really need the fglrx driver and the ati OS driver installed by default should work OK with beryl as long as direct rendering is enabled.  **glxinfo** should tell you if it is.

---

### Post by ownedbyhleb on 2007-06-14
Danke!

Will try when I get some spare time, will post how it goes. =)

---

### Post by tcrroadie on 2007-06-14
Hi ownedbyhleb,

If you are using Feisty Fawn 7.04, you should have everything you need already installed on your system. 

As ownedbyhleb stated, you really do not need the ATI fglrx driver to have Compiz or Beryl working on your system.  

Your xserver should already be configured to use the open source ATI driver set.  If you view the "Device" section of your xorg.conf file it should allready have the driver "ati" set for you.  The driver "ati" will automatically load the Radeon diver module for your video card if it detects a Radeon card in your system.  If you like, you can replace "ati" with "radeon".  

```
Driver      "radeon"
```

Compiz is preinstalled on Feisty.  To start Compiz, you can enable it in your Gnome Preferences menu.  

System -> Preferences -> Desktop Effects  

I would also recommend reading the comminity RadeonDriver document found at the link below.  

[RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

You can also free up some memory for your system buy disabling any unwanted services in you Gnome -> System -> Administration -> Services menu.  

Hope this helps.  Good luck.  :)

---

