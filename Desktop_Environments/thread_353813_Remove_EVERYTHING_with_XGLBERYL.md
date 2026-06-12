---
title: "Remove EVERYTHING with XGL/BERYL"
date: 2007-02-05
forum: Desktop Environments
---

### Post by shador on 2007-02-05
Could someone please help me with removing everything that has to do with beryl and XGL from my computer. Would like to start over so to speak.

---

### Post by ffxr on 2007-02-05
to remove beryl:

```
sudo apt-get --purge remove beryl beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings beryl-settings-bindings beryl-vidcap emerald libberyldecoration0 libberylsettings0 libemeraldengine0


sudo apt-get autoremove
sudo apt-get autoclean
rm -r ~/.beryl

rm -r ~/.emerald
rm -r ~/.beryl-managerrc
```

dunno about XGL.. its abit of a handlin afaik.. & it will probably depend on how exactly u installed it..  i just decided to reinstall my entire OS.

---

### Post by shareMenaPeace on 2007-02-05
Check 

System -> Administration -> Synaptic Package Manager 

Search here for "beryl" and UN-checkbox all "beryl" parts to uninstall beryl.

---

### Post by CosmicTwinky on 2007-02-15
I'm with shador on this one.  I installed everything exactly the way that it's written, but, for some reason it still won't work.  :(  So, like any linux user, I'm going to learn from the experience and try, try again!  heheh

---

### Post by Robor on 2007-02-15
> **shareMenaPeace said:**
> Check 

System -> Administration -> Synaptic Package Manager 

Search here for "beryl" and UN-checkbox all "beryl" parts to uninstall beryl.

^^^  That worked for me as well.  ^^^  I think I right clicked and selected 'completely remove'.

I had beryl & aixgl working fine then I applied an update on Monday or Tuesday.  After I restarted I got my desktop but if I launched an app (say gnome-terminal) it would launch in the upper left of the screen without a border at the top (no title bar and no minimize, full screen, close buttons).  Seems with beryl, if it ain't broke don't fix it.  ;)

I tried doing 'apt-get remove beryl' and it auto-removed it a bunch of other stuff (beryl-settings, emerald, etc).  I then removed the ~/.beryl and ~/.emerald directories and removed 'beryl-settings' from my startup.

I went into Synaptic and searched for 'beryl' and unchecked everything green and rebooted.  Now I'm back go regular Gnome.

---

### Post by saeid on 2007-03-03
Thanks **ffxr**;

---

### Post by JC Denton on 2007-03-17
I installed beryl and it looked fine before restarting. However, after restarting it failed to work.

I have now removed everything beryl related (from within Synaptic pck. man.) but I cannot get my nVidia drivers to work again. Whenever I set my device driver to nvidia instead of nVidia the xserver cannot find any monitor according to the error message.

I have even used the Xorg.conf backup created by the install script. Nvidia drivers were also reinstalled using Automatix. Card is a Nvidia geForce 2 mx 400 w/ 64mb.

I don't care too much for getting beryl to work again although it looked sweet. I would first like to get my nvidia drivers going again.

Also, it wrecked my AMSN installation which will not start again. TCK not found or something similar.

Thank you for your help.

[Ubuntu 6.10]

---

### Post by rico001 on 2007-03-21
JC

Here are some nvidia xorg settings:
I have a PCI  GeForce2 MX400 w32mb of RAM
For the drivers I used envy, it helps to install the nvidia drivers

You will have to customize it for your own needs
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
#amount of ram
        VideoRam        64000  
#Option to make sure no agp is detected.
        Option  "NvAgp"   "0"
#No nvidia logo
        Option  "NoLogo"   "1"
EndSection

to configure xserver
sudo dpkg-reconfigure xserver-xorg

Remember to make backup of xorg.conf
cp  /etc/X11/xorg.conf  /etc/X11/xorg.conf.nvidia

If you get a black screen.  But hear a beep meaning your at the login screen.

You can use Ctrl+Alt (F1-F6) to login to the console.

Then after you login you can do 

sudo nano /etc/X11/xorg.conf to edit the config file manually.

You might also have to pick a different session for your display manager.

watch out for Gunther :)

---

### Post by JC Denton on 2007-03-24
Thanks for the reply rico001

I replaced the device section with your suggestion and commented out glx from the loadmodules (I recall adding this) but the same error occurs. (No output device) Will I need to run 
sudo dpkg-reconfigure xserver-xorg
After modifying the config file?

Also, I'm not unfamiliar with modifying my config file in the console/run level. I have set the driver to nv countless times by now ;-)

No worries about Gunther. His p/w still is zeitgheist IIRC ;-)

---

### Post by Hangly on 2007-04-01
> **Robor said:**
> ^^^  That worked for me as well.  ^^^  I think I right clicked and selected 'completely remove'.

I had beryl & aixgl working fine then I applied an update on Monday or Tuesday.  After I restarted I got my desktop but if I launched an app (say gnome-terminal) it would launch in the upper left of the screen without a border at the top (no title bar and no minimize, full screen, close buttons). 


The same thing happened to me.  What was in that update that broke everything?

---

### Post by JC Denton on 2007-04-05
> **JC Denton said:**
> Thanks for the reply rico001

I replaced the device section with your suggestion and commented out glx from the loadmodules (I recall adding this) but the same error occurs. (No output device) Will I need to run 
sudo dpkg-reconfigure xserver-xorg
After modifying the config file?

Also, I'm not unfamiliar with modifying my config file in the console/run level. I have set the driver to nv countless times by now ;-)

No worries about Gunther. His p/w still is zeitgheist IIRC ;-)

As of yet I'm still without my nVidia drivers. Any solution? extreme (repair) or otherwise?

Many thanks

---

