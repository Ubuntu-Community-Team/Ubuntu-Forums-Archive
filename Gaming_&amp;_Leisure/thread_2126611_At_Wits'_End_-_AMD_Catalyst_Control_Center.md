---
title: "At Wits' End - AMD Catalyst Control Center"
date: 2013-03-17
forum: Gaming &amp; Leisure
---

### Post by seande on 2013-03-17
Hello everyone, I recently built a budget system and decided to welcome Ubuntu as my Operating System. I have installed 12.04 and 12.10 at least ten times at this point. I feel that I have a decent grasp of how Ubuntu works now, from all of this work. My primary concern: AMD Catalyst Control.

My hardware:
Core i3 3220
AsRock Pro3 Z75
8GB DDR-1600 RAM
XFX Radeon 7770 at 1095GHz

I have attempted to install the drivers as per the [Wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide"), and even used methods such as [this]("http://steamcommunity.com/app/221410/discussions/0/864960354325873942/"), getting the 13.1 beta onto the 3.4 kernel. Everything works fine for awhile until I begin getting system errors and am forced to purge the drivers or reinstall. Right now, I have the 13.1 beta drivers (which worked better and for longer than the released drivers). However, now I boot up to a black screen - sometimes with a cursor, sometimes with an X - that has a black border as if overscan is on again. It will boot up if I revert to a previous kernel, 3.5.2 (I believe), but the system is very unresponsive and a system error of amdccc (again, I believe) pops up. 

The whole thing is very annoying, as this has been going on for about a week. It runs for few reboots, and then the problems strike again. Is there anyone who can offer my some guidance or perhaps even a solution? I really don't want to fork my money over to Microsoft, as I really like what Ubuntu offers, but I truly hate the driver support, or at least how I am going about installing them. Thank you guys!

---

### Post by deadflowr on 2013-03-17
I don't think you needed to downgrade the Xserver, or installed a different kernel.
The card you've listed should be supported for existing kernels and Xserver.
The method of installation you've linked is for older cards, from the 4XXX series down, which aren't supported for the latest Xserver.

Did you try installing the drivers from the Ubuntu(restricted) repos?

---

### Post by Ximaceo on 2013-03-17
Hi seande,

The last estable AMD video driver is 13.1
The beta is 13.2

This is how I do:
-First full update Ubuntu, the last kernel is 3.5.0-25-generic.
-Download AMD Catalyst 13.1 Propietary driver from: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)
-Unzip video driver. A new file .run will be created.
-Then click right botton on the file .run and click again on Properties.
-You will open a new window. Then follow these steps:
-Select the Permission tab and click on 'to allow execute the file as a program'
-Now double click on the file .run and install.

Works fine for me.

Please mind that Im spanish and this is a traslation ;)

---

### Post by seande on 2013-03-17
> **Ximaceo said:**
> Hi seande,

The last estable AMD video driver is 13.1
The beta is 13.2

This is how I do:
-First full update Ubuntu, the last kernel is 3.5.0-25-generic.
-Download AMD Catalyst 13.1 Propietary driver from: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)
-Unzip video driver. A new file .run will be created.
-Then click right botton on the file .run and click again on Properties.
-You will open a new window. Then follow these steps:
-Select the Permission tab and click on 'to allow execute the file as a program'
-Now double click on the file .run and install.

Works fine for me.

Please mind that Im spanish and this is a traslation ;)

Okay, so far it seems to work. However, I have a previous version of fglrx. How do I remove that? I attempted:
```
sudo apt-get purge fglrx*
```
and the terminal said it could not find any packages.
I also uninstalled amdccc via synaptic package manager, wheter or not that was a good idea, I don't know. :( Tips?
> **deadflowr said:**
> I don't think you needed to downgrade the Xserver, or installed a different kernel.
The card you've listed should be supported for existing kernels and Xserver.
The method of installation you've linked is for older cards, from the 4XXX series down, which aren't supported for the latest Xserver.

Did you try installing the drivers from the Ubuntu(restricted) repos?
No, I do not believe I have tried that method yet either. How does that work?

---

### Post by Kixtosh on 2013-03-17
> **Ximaceo said:**
> Hi seande,

The last estable AMD video driver is 13.1
The beta is 13.2

This is how I do:
-First full update Ubuntu, the last kernel is 3.5.0-25-generic.
-Download AMD Catalyst 13.1 Propietary driver from: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)
-Unzip video driver. A new file .run will be created.
-Then click right botton on the file .run and click again on Properties.
-You will open a new window. Then follow these steps:
-Select the Permission tab and click on 'to allow execute the file as a program'
-Now double click on the file .run and install.

Works fine for me.

Please mind that Im spanish and this is a traslation ;)
Thank you very much! This also worked for me so your translation is obviously quite good! Note that I had to:

[LIST=1]
[*]Choose the option to run in terminal (not just run) when I double-clicked, since it must be run as super user, and that way I am asked for the password at the appropriate time. 
[*]I had to remove the Additional Drivers for I had already installed via the System Settings (there's an icon in the Unity launcher for that by default, but it can also be found by a seach in Dash home). I've added an image below. 
[*]I also had to remove some stuff I had already tried with the wiki, using the command in the quote below. 
[/LIST]
 ```
sudo apt-get purge fglrx*
```

An error message was returned, but apparently it worked anyway.

**EDIT: Forgot to mention, this is for an ATI Mobility Radeon HD 5400 Series (5430) in an Arctic MC-001 with Precise Pangolin 12.04.**

---

### Post by Ximaceo on 2013-03-17
> **seande said:**
> Okay, so far it seems to work. However, I have a previous version of fglrx. How do I remove that? I attempted:
```
sudo apt-get purge fglrx*
```
and the terminal said it could not find any packages.
I also uninstalled amdccc via synaptic package manager, wheter or not that was a good idea, I don't know. :( Tips?

No, I do not believe I have tried that method yet either. How does that work?

Sorry, but I am a new user in Ubuntu. I don't know how to remove the previous version of fglrx.

---

### Post by seande on 2013-03-17
I eventually reinstalled, as I figured the automation would be easier than fixing what I broke. So far it's installed and seems to be working. No crashes yet either. Hoping it all goes well. Why did nothing I search for turn up something this easy? You have no idea how much I appreciate this. Thank you so much!

---

### Post by Ximaceo on 2013-03-17
> **seande said:**
> I eventually reinstalled, as I figured the automation would be easier than fixing what I broke. So far it's installed and seems to be working. No crashes yet either. Hoping it all goes well. Why did nothing I search for turn up something this easy? You have no idea how much I appreciate this. Thank you so much!

You're welcome. :)

---

### Post by Kixtosh on 2013-03-17
> **seande said:**
> I eventually reinstalled, as I figured the automation would be easier than fixing what I broke. ...Been there! Done that! I think it's probably not very hard to figure out how to undo stuff that has been done and may not have worked as intended, such as the "purge" command I showed above, but for new users it's frequently more reassuring to just start over, since installing and updating from scratch only takes about an hour (including udpdates).

> ... You have no idea how much I appreciate this. Thank you so  much!I know how much you appreciate it, believe me, so many thanks our Spanish speaking friend and colleague, and thanks also to you for posting the thread, since your quest proved to solve my problem as well!

One thing to be careful about is how old some articles are. Sometimes, you'll find troubleshooting tips that have nothing to do with current releases, so try to find a date on anything you use, and ignore anything prior to 12.04 (the most recent LTS version using Unity) unless you have figured out why it might work. In the case of that earlier solution you posted a link for ([http://steamcommunity.com/app/221410/discussions/0/864960354325873942/](http://steamcommunity.com/app/221410/discussions/0/864960354325873942/)), that person was using an ATI Mobility Radeon HD 4200 Series card, and those are no longer supported, which is why he was downgrading his system from the kernel version and the latest xorg-xserver version.

---

### Post by Ximaceo on 2013-03-17
> **Kixtosh said:**
> I know how much you appreciate it, believe me, so many thanks our Spanish speaking friend and colleague, and thanks also to you for posting the thread, since your quest proved to solve my problem as well!

Im happy for you too Kixtosh :guitar:

---

### Post by Kixtosh on 2013-03-17
> **seande said:**
> Okay, so far it seems to work. However, I have a previous version of fglrx. How do I remove that? I attempted:
```
sudo apt-get purge fglrx*
```
and the terminal said it could not find any packages. ...So, since this thread has been successful for at least two of us, it might be useful for other users who might also be at their wits' end (like seande), and might also find this post through a search (like me), to post this information from another source about removing old drivers. 

If this does not work: ```
sudo apt-get purge fglrx*
``` Remember that the error message that I also got might not matter, then you could try this procedure:
> Uninstall first the old driver with the following commands:
 
[B]sudo sh /usr/share/ati/fglrx-uninstall.sh
[B]
**sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx**[/B][/B]

This is from the link below, which is about installing an OLDER driver (12.8) than currently available (13.1), but the removal method might still be valid. I did NOT have to do this and have not tried it, so use at your own risk!

[http://www.upubuntu.com/2012/08/install-amd-catalyst-128-on-ubuntu.html0](http://www.upubuntu.com/2012/08/install-amd-catalyst-128-on-ubuntu.html0)

---

### Post by Ernesto M EF on 2013-03-21
I hear you.. i had the same issue but i think its catalyst i mean i try to resize my screen to fit FULL 1080 and catalyst cant even resize the screen entirely even if i hit apply the thing will remain in its form untill i reboot the system back to being a small box in the center of my screen.. bummer.

If drivers dont install right i went through this like crazy in my first attempt to installing my ATI RADEON 5000 series to my Ubuntu and went online to see if anyone could help and there solutions never helped so i reinstalled the OS and restarted the system and tried to check the Additional Drivers "For some odd reason in the very first use Ubuntu would not recognize my Graphics Card" and surprisingly it recognized it and went through the entire install download hubblah.. Next i wanted to play on Steam and it recommended to use the Experamental drivers instead of the stable so i went through it "I wasnt ok with it i mean its a experament" but so far my system runs ,y Graphics Card wonderful.

---

### Post by Kixtosh on 2013-03-21
> **Ernesto M EF said:**
> ... i had the same issue but i think its catalyst i mean i try to resize my screen to fit FULL 1080 and catalyst cant even resize the screen ...Catalyst has been able to resize the screen for me:


[LIST]
[*] On a 19" LCD monitor with VGA, 
[*]On a 37" LED TV with HDMI, 
[*]On both the former connected and resized correctly at the same time, 
[*]And on a 46" LCD TV with HDMI. 
[/LIST]
 
> **Ernesto M EF said:**
> ... i  reinstalled the OS and restarted the system and tried to check the  Additional Drivers ...Remember that, according to the instructions that have worked for some of us, it is NOT possible to use the built in search for Proprietary Hardware Drivers. If that method was attempted already, then those will have to be purged with a command line interface, and then the correct drivers downloaded from AMD and installed, also using the command line interface as described earlier.

---

### Post by R33D3M33R on 2013-03-22
I have a HD7750 on 12.10 AMD64 and I always install via .deb packages built from the .run file: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Create_and_install_.deb_packages](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Create_and_install_.deb_packages) 
Currently I have 13.1 installed and they work flawlessly from day one.

Remember, always run: 
```
sudo amdconfig --initial
``` or ```
sudo aticonfig --initial
``` after installing.

---

### Post by Kixtosh on 2013-03-22
> **R33D3M33R said:**
> ... [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Create_and_install_.deb_packages](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Create_and_install_.deb_packages) ...
That link is a great resource for Quantal Quetzal (12.10). I was able to use some of the information in Precise Pangolin 12.04 LTS, especially to add XvBA to XBMC, which seems to be the appropriate choice for video acceleration for the ATI Mobility Radeon HD 5430 graphics on my Arctic MC001 Media Centre. Only VDPAU, which is for Intel as far as I know, and VAAPI were available by default, but the specific OpenELEC distro (dedicated XBMC, for those who are not familiar with it, without anything else, so no applications or web browser etc.) for this mini desktop uses only XvBA as well.

```

sudo apt-add-repository ppa:wsnipex/xbmc-xvba 
sudo apt-get update 
sudo apt-get install xbmc 
```

---

