---
title: "The new X lacking an xorg.conf"
date: 2009-04-16
forum: General Help
---

### Post by k420 on 2009-04-16
Using Jaunty and my xorg.conf is blank where do i edit it now.  I can not install my nvidia driver until i figure htis out and even then i probably wont be able to until nvidia changes there driver.

---

### Post by Therion on 2009-04-16
There were some pretty massive changes in the X system starting with Intrepid and now the xorg.conf file is utilized far, far less.  This is somewhat of a mixed blessing IMO.

At any rate, what prevents you from installing the nVidia restricted driver with the installed Driver Manager?  That would be the suggested method.

---

### Post by k420 on 2009-04-16
If install it from the manager X will not come back up it looks for files in the xorg.conf file and nothing is there.  It says that I am missing a bunch of font files and there are no devices.  Far as i can tell the Nvidia driver trys to nmake all of its changes to the xorg.conf file which is not even there. Off of a new install I update the system then i click the restricted driver manager thingy and install the nvidia driver  it gets done then i have no X.

---

### Post by Therion on 2009-04-16
Okay, something's not right here.  Can you cat your xorg.conf file and post the output here?

The new .conf file in JJ is certainly... brief... in comparison to previous versions, but you should still have one.

---

### Post by k420 on 2009-04-16
> cat: xorg.conf: No such file or directory


So i have no freaking clue.  Oh and just to clarify i am on Jaunty

---

### Post by Therion on 2009-04-16
> **k420 said:**
> So i have no freaking clue.  Oh and just to clarify i am on Jaunty
What I was asking was for you to post the contents of your xorg.cong file.  You can use the editor or you can use the cat (catalog) command to get the output.  Sorry if I confused you.  

Just use nano and Copy & Paste your xorg.conf file here so I can see what you're looking at.  Or NOT looking at, as the case may be.

---

### Post by k420 on 2009-04-16
If it is still  /etc/X11/xorg.conf  than it is blank.  I am in gnome right now though.  And I have edited xorg.conf plenty of times so I am not doing it wrong.
 Thankyou for your help this is very confusing for me

---

### Post by Therion on 2009-04-16
Have you tried rebooting your PC and going into "Recovery Mode" and using **xfix**?

From what I understand, it's possible to have X running correctly even without an xorg.conf file so I'd actually prefer not to mess with that if we don't have to.

---

### Post by k420 on 2009-04-16
no i havent tried that yet
and I am in the same boat I need to have a working pc. but i also need to get the nvidia driver working as I have 2 9600 gt's in this box and i really dont want them to go to waste.  Plus i am a GTA4 fiend

---

### Post by doas777 on 2009-04-16
I think that is the one case where ```
sudo dpkg-reconfigure xserver-xorg
``` would still be useful.
give it a try and check your xorg.conf again. it should contain device and font info (but no real video config).

as close as I can tell, all vid info is discovered and set via xrander at boot, so after you get x fixed, if you need further custom video configuration, an xrander script may do ya.

---

### Post by Therion on 2009-04-16
> **k420 said:**
> no i havent tried that yet
and I am in the same boat I need to have a working pc. but i also need to get the nvidia driver working as I have 2 9600 gt's in this box and i really dont want them to go to waste.  Plus i am a GTA4 fiend
This *sounds* totally fixable.  Try pressing Escape at boot menu, selecting Rescue Mode and running xfix.  I'm hoping that will straighten things out for you.

---

### Post by k420 on 2009-04-16
> **Therion said:**
> This *sounds* totally fixable.  Try pressing Escape at boot menu, selecting Rescue Mode and running xfix.  I'm hoping that will straighten things out for you.

Should i install nvidia first

---

### Post by k420 on 2009-04-16
> **doas777 said:**
> I think that is the one case where ```
sudo dpkg-reconfigure xserver-xorg
``` would still be useful.
give it a try and check your xorg.conf again. it should contain device and font info (but no real video config).

as close as I can tell, all vid info is discovered and set via xrander at boot, so after you get x fixed, if you need further custom video configuration, an xrander script may do ya.

Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

---

### Post by HankB on 2009-04-16
> **k420 said:**
> If it is still  /etc/X11/xorg.conf  than it is blank.  I am in gnome right now though.  And I have edited xorg.conf plenty of times so I am not doing it wrong.
 Thankyou for your help this is very confusing for me

X configuration is now apparently done using XML files with the .fdi extension. This has been the case since Intrepid. My install has an xorg.conf, but it was practically empty and anything added to it seemed to be ignored. I think I managed to solve a problem with by synaptics touchpad by creating the file
```
/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
```

At present this seems to be a pretty well kept secret. I had a lot of difficulty finding any information on it and AFAIK, there is no tool included to help manage the settings kept in these files.

Good luck.

-hank

---

### Post by Therion on 2009-04-16
> **k420 said:**
> Should i install nvidia first
Can't hurt to try.  Use the Hardware Manager and see what it tells you.  If it works, great...  If not, reboot into Recovery Mode and try xfix.  
Then go back to the Hardware Manager and try again.

If none of this works, I'm not sure what to tell you besides a fresh install.  I'd wait before doing that, though, too see if someone else has some other ideas to try.

---

### Post by k420 on 2009-04-16
Ok xfix did not fix it.  The error msg i got was that the primary device is not PCI which it is not it is 
PCIe.  What can i change in the xorg.conf to fix that

---

### Post by k420 on 2009-04-16
Si added to the device field in xorg.conf which i have a mega genmeric one now.  > BusID		"PCI:a:0:0"  I got this from lspci it was 0a:0.0
> Option		"BusType"	"PCIE"
still no luck

---

### Post by Daisuke_Aramaki on 2009-04-16
If setting up nvidia card alone is the issue, then do this.

Download the nvidia driver of your card directly from nvidia website. if you are already in a desktop environment and assuming you use gdm. do this.

```
sudo /etc/init.d/gdm stop
```

it will take you the commandline.

The driver you downloaded will be NVIDIA-somename.pkg1.run.

Then issue this command

```
sh NVIDIA-somename-pkg1.run
```

You will be presented with a license acceptance screen. click yes and the driver will be built and the xorg.conf will be automatically generated. it will also install a nice nvidia interface to configure refresh rates, dual heads etc.

Once the install is done and the xorg.conf file is generated. do this

```
sudo /etc/init.d/gdm start
```

You will be taken back to gdm and you can login.

On a related note, it is pretty usual to not have a xorg.conf file at all. But if you have a proprietary card like nvidia, then it might be needed, and also sometimes, some fonts won't be rendered properly unless their paths are set in xorg.conf.

---

### Post by k420 on 2009-04-16
Yeah i have done that numerous times.  doesnt work at all now i have 2 cards in my pc with an sli bridge do you think that could be causing the problem

---

### Post by Daisuke_Aramaki on 2009-04-16
> **k420 said:**
> Yeah i have done that numerous times.  doesnt work at all now i have 2 cards in my pc with an sli bridge do you think that could be causing the problem


wait, you tried installing nvidia driver that way, and so you got an error numerous times? if so, what kind of error did you get? as far as the 2 cards thing go, i don't know.

---

### Post by k420 on 2009-04-16
well i guess i will give up on nvidia for a while  i would go back t vista if ic ould but i got a super nasty virus that lays dormant until it finds an exe to infect and i cant remove it.  I run a computr store thqat specialiizes in it too.  Just screwed i guess

---

### Post by LowSky on 2009-04-16
This tutorial should help

[http://us.download.nvidia.com/XFree86/Linux-x86/180.44/README/part-01.html](http://us.download.nvidia.com/XFree86/Linux-x86/180.44/README/part-01.html)

this part is about SLI mode
[http://us.download.nvidia.com/XFree86/Linux-x86/180.44/README/chapter-25.html](http://us.download.nvidia.com/XFree86/Linux-x86/180.44/README/chapter-25.html)

---

### Post by Daisuke_Aramaki on 2009-04-16
> **LowSky said:**
> This tutorial should help

[http://us.download.nvidia.com/XFree86/Linux-x86/180.44/README/part-01.html](http://us.download.nvidia.com/XFree86/Linux-x86/180.44/README/part-01.html)

this part is about SLI mode
[http://us.download.nvidia.com/XFree86/Linux-x86/180.44/README/chapter-25.html](http://us.download.nvidia.com/XFree86/Linux-x86/180.44/README/chapter-25.html)

i was just about to post the SLI mode link for him. Great that you did it already.

---

### Post by LowSky on 2009-04-16
> **Daisuke_Aramaki said:**
> i was just about to post the SLI mode link for him. Great that you did it already.

Yeah I was suppired no one had posted the instructions. SLi insn't very popular around here I guess. Heck I don't use it either

---

### Post by Daisuke_Aramaki on 2009-04-16
> **LowSky said:**
> Yeah I was suppired no one had posted the instructions. SLi insn't very popular around here I guess. Heck I don't use it either

i guess so.

---

### Post by k420 on 2009-04-16
thankyou very much i will be trying your instructions in a few.  Hopefully id ont have to reinstall again.  I am getting sick of it.I guess maybe i should back up my root folder so then i dont have to keep reinstalling package after package.

---

