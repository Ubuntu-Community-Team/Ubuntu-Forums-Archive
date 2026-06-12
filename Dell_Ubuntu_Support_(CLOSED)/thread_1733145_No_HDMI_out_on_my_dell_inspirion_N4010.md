---
title: "No HDMI out on my dell inspirion N4010"
date: 2011-04-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dhirajv12 on 2011-04-18
Hi,

I have recently installed Ubuntu 10.04.2 on my dell laptop. there is no HDMI output from my PC to the television, I need help as what I can do to watch movies on my HD TV.

Dhiraj

---

### Post by varunendra on 2011-04-19
Please post back the output of
```
sudo lshw -C display
```

Also, check if there is some additional driver available for your display adapter (System > Administration > Hardware Drivers)

---

### Post by dhirajv12 on 2011-04-19
Here is the output

*-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 12
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:30 memory:f0000000-f03fffff memory:d0000000-dfffffff(prefetchable) ioport:1800(size= 8)



And there are no hardware drivers available, I have downloaded one broadcommSTA driver for my wireless, only that is visible.....

---

### Post by varunendra on 2011-04-20
The specs for your lappy model show ATI Radeon 5470 as discrete graphics.

So it seems you need drivers for that interface while currently only the embedded intel graphics is being used.

Before going any further on this, can you please confirm if these are exactly the same specs for your laptop:
[http://www.pcworld.com/product/552981/dell_inspiron_14r_model_n4010.html?p=specs](http://www.pcworld.com/product/552981/dell_inspiron_14r_model_n4010.html?p=specs)

Also, check if there is any setting in BIOS to enable / disable the discrete graphic interface and make sure it is enabled.

---

### Post by dhirajv12 on 2011-04-20
Yes varun its the same laptop.
There are no such bios setting where I need to activate the graphiccs gards...
I guess the drivers are missing, this laptop came with a pre installed windows 7 OS, in which I was able to veiw the vedio and audio out by from the HDMI port. But after I installed ubuntu i had these problems....Now I am trying to install windows iin ubuntu as a virtual machine, and install necessary drivers in windows......this is a not a good idea though....
help me find a way out where i can veiw HD vedio from ubuntu

---

### Post by varunendra on 2011-04-21
Just a quick tip - although not related to original problem:

If you have planned to install windows, then for best performance, instead of installing it in a virtual machine you can install it in parallel with ubuntu (although you will have to reinstall grub boot loader to re-access ubuntu). If it is going to be Win7, its partition will have to be a primary one. You may use gparted from live cd to manage partitions.

I'll post back as soon as I got some specific help for your ATI graphics.

Meanwhile, you may try to enable all the repositories in Synaptic Package Manager > Settings > Repositories > (tick all the check-boxes under 'Ubuntu software'),

then goto System > Administration > Update Manager > Check & update your system.

(Excuse me if this sounds stupid because you might have already tried this, but it just works sometimes)

---

### Post by varunendra on 2011-04-21
With my very limited knowledge and experience, all I could find suggests that radeon hd 5xxx series has long been a headache for linux users, and ATI's support for linux on this series has been worse than poor.

So this leaves you with 3 options (try them in order they are suggested):

[LIST=1]
[*]Enable all repositories as suggested in my above post, then update to see if a proprietary driver comes up for your adapter.
[*]If no driver comes up by default, try fglrx driver from the repositories hoping they have improved support in latest package.
[*]Even if fglrx doesn't work, then you'll have to properly remove it before going any further (! this is important !). Follow this guide to remove it : [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver) . After removing the fglrx driver, you will have to follow this guide to install proprietary drivers : [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)
[/LIST]
The last step requires patience and care while typing commands. It is recommended to copy-paste commands from the above guide to the terminal instaed of typing them to avoid typing mistakes.

However, the last output of **lshw -C display** command worries me a bit, since I thought it should have displayed both of your display adapters assuming that your ATI one has been detected, only just not initialized due to lack of driver. So **if** (let's hope I am wrong) it indicates that your ATI adapter has not been even detected by the kernel then the above methods may not work at all !! But I may be wrong since it is only my assumption and not experience (I've no personal experience with dual adapters).

So let's hope for the best while being prepared for the worst. It pays to learn, but if you are not yet prepared for it, another option would be to just install Windows in parallel for HDMI support until some stable and guaranteed solution for these cards comes up for ubuntu.

---

### Post by brpylko on 2011-04-21
Do you mean the HDMI connector does not work or you have no HDMI connector?

If the latter, buy a VGA/DVI-HDMI converter.

---

### Post by dhirajv12 on 2011-04-22
Varun,
I guess  I need HDMI interface drivers......
Please correct me of I am wrong. ...... Or If i have not put up my problem correctly........... It is like I can watch the HD vedio on my PC on a VLC player, but I cannot output this HD content to my HD TV, My TV does not detect any signal from the HDMI port .

I have a problem with the mike also, even it is not detected on ubuntu , so I uninstalled pulse-audio and reinstalled it, but now I could get nothing when I say system>preferences>sound it keeps serching for devices, and my mike problem is still there............So I am just trying to be careful........if fglrx is the problem I will go ahead and install fglrx all over.... help me

---

### Post by varunendra on 2011-04-22
> **dhirajv12 said:**
> Here is the output

*-display               
       description: VGA compatible controller
       product: [COLOR=Red]**Core Processor Integrated Graphics Controller**[/COLOR]
       vendor: Intel Corporation.....
The highlighted text means you are currently using the " graphics that is 'embedded' into your i3 microprocessor itself, not the dedicated ATI graphics. So you have actually two graphic adapters one of which is (apparently) not detected at all, that is, the ATI adapter.

> **dhirajv12 said:**
> Varun,
I guess  I need HDMI interface drivers......
Please correct me of I am wrong. ...... Or If i have not put up my problem correctly........... It is like I can watch the HD vedio on my PC on a VLC player, but I cannot output this HD content to my HD TV, My TV does not detect any signal from the HDMI port .

I have a problem with the mike also, even it is not detected on ubuntu , so I uninstalled pulse-audio and reinstalled it, but now I could get nothing when I say system>preferences>sound it keeps serching for devices, and my mike problem is still there............So I am just trying to be careful........if fglrx is the problem I will go ahead and install fglrx all over.... help me

You've put your problem quite clearly and in proper manner, but you, it seems, are misinterpreting the functionality of HDMI. It is not a seperate device, just another interface of your ATI graphics. So once you got a fully functional ATI driver for your ATI adapter (which is completely separate and different from your currently working display adapter - the embedded one), you'll not only get far better graphics on your monitor, but also the HDMI port would become functional.

However, the functionality and quality of the ATI adapter would entirely depend upon the quality of the driver (fglrx or the one suggested in the linked guide). fglrx may or may not work. If it doesn't, then you'll have to remove it properly as suggested in the guide, and will have to proceed to build your own deb package and install it - all as given in the guide links.

As for HDMI, I am not yet able to conclude whether or not it is going to work with even the driver suggested in the 3rd point of my previous post. But what I could find in a thorough search suggests that it is the most appropriate (and perhaps guaranteed) method to install proprietary drivers for ATI HD graphics.

---

### Post by dhirajv12 on 2011-04-25
Varun,

Thanks a lot for giving me this information.
I tried the method suggested by you. First uninstall and tried to re install the fglrx catalyst.
During installation I had these problems

for the command  
[B]sudo apt-get install ia32-libs

it shows E: Couldn't find package ia32-libs[/B]

And after creating .deb and installation....
for the command
[B]
sudo aticonfig --initial -f [/B]

it shows  **aticonfig: No supported adapters detected**

And there is no xorg.conf in the folder /etc/X11/


And the output of command** $ fglrxinfo**
Shows ...** Segmentation fault**

What could have been the problem......perhaps " *Unfortunately, there is no sure way to generate the ATI version of the Xorg.conf file. It is entirely dependent on your configuration. The following subsections will attempt to address possible (and tested) variations for their respective configurations*." this line is for my case..........

Suggest me a work around Varun...

---

### Post by dhirajv12 on 2011-04-26
Varun

I have tried to uninstall and install fglrx after following the given steps for istallation I have few errors..
here is the output of the command
[B]sudo apt-get install ia32-libs
E: Couldn't find package ia32-libs[/B]

After i create the .deb and install the output of he following command shows
sudo aticonfig --initial -f
aticonfig: No supported adapters detected

And there is no xconf.org file in the /etc/X11

perhaps the line "Unfortunately, there is no sure way to generate the ATI version of the Xorg.conf file. It is entirely dependent on your configuration. The following subsections will attempt to address possible (and tested) variations for their respective configurations. " is for my case...

Suggest me a work around varun

---

### Post by varunendra on 2011-05-03
Sorry for such a late response. This is getting over my head now and am a bit short of time to have a closer look into the matter.

So I am just replying to bump this thread so that hopefully someone else with better knowledge may pick it up.

Meanwhile, you may try to search the forums for HDMI+ATI based [solved] threads to see if any matches your case. One such search gave me this:
[http://ubuntuforums.org/showthread.php?t=1705984&highlight=HDMI%2C+ATI](http://ubuntuforums.org/showthread.php?t=1705984&highlight=HDMI%2C+ATI)
which mentions this link as a working method:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Again, sorry for not being able to guide you through the process.

..
BUMP !
..

---

