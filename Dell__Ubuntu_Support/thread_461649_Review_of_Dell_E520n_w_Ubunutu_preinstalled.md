---
title: "Review of Dell E520n w/ Ubunutu preinstalled"
date: 2007-06-01
forum: Dell  Ubuntu Support
---

### Post by mrowen on 2007-06-01
First, see the 410 review as the startup and disk lay out are similar. I just received my Dell E520n with Ubuntu today. I'm typing this message on it now. I was delighted to find stock Ubuntu installed without any sort of Dell-ization of the OS. An Ubuntu CD was included with my system. I opted for the Nvidia 7300 card with mine and a 1680X1050 wide screen panel display. It booted up in 1024x768 mode. I used Automatix to grab the correct Nvidia drivers and soon had full resolution support. So far I am very pleased with the machine and the display. Here are the partitions as configured by Dell. See the Dell 410 review for details.

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2               7         268     2104515    b  W95 FAT32
/dev/sda3   *         269         293      200812+  83  Linux
/dev/sda4             294       30394   241786282+   f  W95 Ext'd (LBA)
/dev/sda5             294         774     3863601   82  Linux swap / Solaris
/dev/sda6             775       30394   237922618+  83  Linux

The only Issue that I am having right now is getting the screen resolution to be set properly at startup time. This is probably an xorg.conf issue. I am about to investigate a reboot issue. When doing a restart of the system, it seems to hang at the splash screen on its way back up. The splash screen appears, but the progress bar never even begins to turn orange. I came across a post referencing the Nvidia splash screen causing issues with this. Again, I have to look into it further.

Specs:

Dimension E520n  Intel® Core™ 2 E6420 Duo Processor(4MB L2 cache,2.13GHZ,1066FSB)
Memory 	4GB Dual Channel DDR2 SDRAM at 667MHz- 4DIMMs
Monitor 20 inch E207WFP Widescreen Digital Flat Panel
Video Cards    256MB nVidia Geforce 7300LE TurboCache
Hard Drives 	250GB Serial ATA Hard Drive (7200RPM) w/DataBurst Cache™
Operating System 	Ubuntu Desktop Edition version 7.04
Network Interface 	Integrated 10/100/1000 Ethernet
CD or DVD Drive 	48X CD-RW/ DVD Combo Drive
Sound Cards 	Integrated 7.1 Channel Audio

---

### Post by magicfab on 2007-06-01
Just a friendly reminder, as soon as you start using tools like Automatix, we can't offer much support based on all the changes done to the standard install.

Cheers,

---

### Post by mrowen on 2007-06-01
Just a quick update regarding my resolution problem on the E520n. All I had to do was edit the /etc/X11/xorg.conf  file to specify the 1680x1050 resolution. As I stated earlier, I installed the Nvidia drivers via Automatix. I am using the nvidia and not the nv device. The Nvidia utility lets me set the resolution and has a button to save settings to xorg.conf. However, this seems to write only 1024 to the file. Here is the relevant section of the xorg.conf file in case anyone needs it. I only changed the "Modes" lines. 

Section "Device"
    Identifier     "nVidia Corporation GeForce 7300 LE"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation GeForce 7300 LE"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection
EndSection

---

### Post by MepisReign on 2007-06-01
Hi:

Open a terminal and type

sudo nvidia-settings

Make the changes, save it pressing Save to xorg.conf

That way the changes should remain after the system gets reboot

Regards

MepisReign

---

### Post by mailbinoy on 2007-06-02
running nvidia-settings with root privileges should  do the trick

sudo nvidia-settings

---

### Post by mrowen on 2007-06-02
Yes, that is what I was doing and clicking on the button to save the settings, but they were not written to the xorg.conf file. It still had 1024x780 in the file. So I just edited it manually. Perhaps the nvidia-settings utility is writing them somewhere else? I don't know.

---

### Post by mrowen on 2007-06-02
I mentioned that I am having an issue with restart. I tested a bit more. Shutdown works properly. It is only restart that seems to get stuck. I can't really tell if its stalling when its stopping or restarting. Whenever I choose restart, I have to manuallypower the system off. A glanced at the syslog, but nothing is jumping out at me. Its late, so I'll pick it up in the morning. I'm open to suggestions. This is a new system, so I'm willing to even reinstall if that is a recommendation.

---

### Post by MepisReign on 2007-06-02
It is most probably related to the driver from automatix
In my case I'm running Kubuntu 7.04 on a Dell XPS 400 and I just installed nvidia-glx-new with synaptic, then checked on xorg for the word "nvidia" under Device, reboot and boom! perfect resolution on the screen :p

In any case I'm glad that you solved that little glitch...

MepisReign

---

### Post by tgalati4 on 2007-06-02
Make sure your vertical and horizontal refresh rates are correct in xorg.conf.  Try using a large range of values for both to allow better resolution detection.

---

### Post by octathlon on 2007-06-02
> **mrowen said:**
>  I opted for the Nvidia 7300 card with mine and a 1680X1050 wide screen panel display. It booted up in 1024x768 mode. 

So the monitor and video card were standard options that you bought from Dell, and they weren't configured to work out of the box? That's not a good sign.  And are you saying that the nvidia driver wasn't even pre-installed? :(

---

### Post by robgig1088 on 2007-06-02
> **octathlon said:**
> So the monitor and video card were standard options that you bought from Dell, and they weren't configured to work out of the box? That's not a good sign.  And are you saying that the nvidia driver wasn't even pre-installed? :(

I thought that was strange as well.  I understand that the closed-source driver wasn't installed, but the incorrect resolution...?

---

### Post by gwbennett on 2007-06-02
What's Ubunutu?

---

### Post by robgig1088 on 2007-06-02
> **gwbennett said:**
> What's Ubunutu?
From the Ubuntu web site...
> 
Ubuntu is a community developed, linux-based operating system that is perfect for laptops, desktops and servers. It contains all the applications you need - a web browser, presentation, document and spreadsheet software, instant messaging and much more.


Basically, its another operating system (similar to Windows or OS X).  Look at [www.ubuntu.com](www.ubuntu.com) for more information

---

### Post by wormser on 2007-06-02
> **gwbennett said:**
> What's Ubunutu?

It is a linux operating system.  Take a look at the [Ubuntu]("http://www.ubuntu.com/") site.

---

### Post by orrorin on 2007-06-02
> **mrowen said:**
> 

Specs:

Dimension E520n  Intel® Core™ 2 E6420 Duo Processor(4MB L2 cache,2.13GHZ,1066FSB)
Memory 	4GB Dual Channel DDR2 SDRAM at 667MHz- 4DIMMs
Monitor 20 inch E207WFP Widescreen Digital Flat Panel
Video Cards    256MB nVidia Geforce 7300LE TurboCache
Hard Drives 	250GB Serial ATA Hard Drive (7200RPM) w/DataBurst Cache™
Operating System 	Ubuntu Desktop Edition version 7.04
Network Interface 	Integrated 10/100/1000 Ethernet
CD or DVD Drive 	48X CD-RW/ DVD Combo Drive
Sound Cards 	Integrated 7.1 Channel Audio

So how much of the 4GB RAM does your system actually recognize/use?

---

### Post by MepisReign on 2007-06-02
> **robgig1088 said:**
> I thought that was strange as well.  I understand that the closed-source driver wasn't installed, but the incorrect resolution...?

Remember that you installed the Nvidia driver from Automatix, the case would be different if you choose the official driver from the repos. As I stated on a previous post what I would recommend is to install it by typing:
sudo apt-get install nvidia-glx-new

But you need to uninstall the automatix driver first of course...

I'm not too familiar with Gnome but that worked for me perfectly on Kubuntu and I had the same video card ( I replaced it with the 7900 GS since I'm a gamer :p )

Best Wishes

MepisReign

---

### Post by psyopper on 2007-06-02
One would think, considering it's in the official repositories, that Dell would pre-install nvidia-glx-new for their boxes shipping with nVidia cards...

---

### Post by MepisReign on 2007-06-02
> **psyopper said:**
> One would think, considering it's in the official repositories, that Dell would pre-install nvidia-glx-new for their boxes shipping with nVidia cards...

That's exactly my concern. I just mailed Dell regarding this issue

MepisReign

---

### Post by ageilers on 2007-06-02
With the Nvidia drivers being proprietary drivers not officially supported by Ubuntu, I doubt Dell would install them. Otherwise, they would already be on the Ubuntu Live CD.

---

### Post by madman91 on 2007-06-02
> **mailbinoy said:**
> running nvidia-settings with root privileges should  do the trick

sudo nvidia-settings

This might not save properly. Try gksudo nvidia-settings

When I ran it with sudo, it never saved properly.

---

### Post by doublecheese on 2007-06-02
Hi.  First post here as I just got my Dell E520n w/Ubuntu today.  Upon booting the machine for the first time I could not get any resolution higher than 1024x768.  Thus, the machine did not work as advertised out of the box.  BUT if you use the ubuntu restore image it works just fine with no configuration needed.  Weird.

Don't ask how I know about restoring already....  :p

---

### Post by arnieboy on 2007-06-02
> **MepisReign said:**
> Remember that you installed the Nvidia driver from Automatix, the case would be different if you choose the official driver from the repos. As I stated on a previous post what I would recommend is to install it by typing:

You are wrong.. and the bigger problem is you are confidently giving wrong advice.. 

Automatix detects the make and model of your card and installs the relevant version of the nvidia driver from the official ubuntu repositories. Remember: nvidia-glx-new will not work for all nvidia cards... do some research or ask on the automatix forums and we will explain why.

as for ubuntu's inbuilt restricted-drivers-manager it fails more often than it works.

---

### Post by nutz on 2007-06-03
> **mrowen said:**
> Yes, that is what I was doing and clicking on the button to save the settings, but they were not written to the xorg.conf file. It still had 1024x780 in the file. So I just edited it manually. Perhaps the nvidia-settings utility is writing them somewhere else? I don't know.


I have noticed this too. Who knows where it is writing it to but it isn't the xorg.conf.

---

### Post by mifi on 2007-06-04
> **mrowen said:**
> I mentioned that I am having an issue with restart. I tested a bit more. Shutdown works properly. It is only restart that seems to get stuck. I can't really tell if its stalling when its stopping or restarting. Whenever I choose restart, I have to manuallypower the system off. A glanced at the syslog, but nothing is jumping out at me. Its late, so I'll pick it up in the morning. I'm open to suggestions. This is a new system, so I'm willing to even reinstall if that is a recommendation.
Have a look at [http://ubuntuforums.org/showthread.php?t=461028]("http://ubuntuforums.org/showthread.php?t=461028").

It was suggested to add "reboot=b" to the end of the kernel line in /boot/grub/menu.lst.

I can confirm this workaround is working for me.

mifi

---

### Post by mdz on 2007-06-04
> **mrowen said:**
> First, see the 410 review as the startup and disk lay out are similar. I just received my Dell E520n with Ubuntu today. I'm typing this message on it now. I was delighted to find stock Ubuntu installed without any sort of Dell-ization of the OS. An Ubuntu CD was included with my system. I opted for the Nvidia 7300 card with mine and a 1680X1050 wide screen panel display. It booted up in 1024x768 mode. I used Automatix to grab the correct Nvidia drivers and soon had full resolution support. 

Could someone confirm that System->Administration->Restricted Drivers Manager works fine in this configuration?  This is the officially supported method of installing the nvidia drivers, and is even simpler to access than third-party tools like Automatix.

---

### Post by mifi on 2007-06-04
> **mdz said:**
> Could someone confirm that System->Administration->Restricted Drivers Manager works fine in this configuration?  This is the officially supported method of installing the nvidia drivers, and is even simpler to access than third-party tools like Automatix.
I can. It does.
mifi

---

### Post by mrowen on 2007-06-04
Thanks mifi! Adding the reboot=b to the grub menu.lst file did indeed fix the issue with the E520n reboot hanging. Thanks for the tip!

---

### Post by matthew on 2007-06-04
> **arnieboy said:**
> as for ubuntu's inbuilt restricted-drivers-manager it fails more often than it works.I'm curious...do you have evidence to substantiate that statement, or is that just your opinion? I have heard very few complaints about the restricted-drivers-manager.

---

### Post by FredSambo on 2007-06-04
> **matthew said:**
> I'm curious...do you have evidence to substantiate that statement, or is that just your opinion? I have heard very few complaints about the restricted-drivers-manager.

It fails for me.  I have an old ATI Radeon 9200 and the Restricted Drivers Manager doesn't detect it.  I had to manually install the fglrx driver using the Edgy instructions [ located here](https://help.ubuntu.com/community/BinaryDriverHowto/ATI).

Of course I should be ashamed of myself for using such an old and crappy video card.  :p

---

### Post by matthew on 2007-06-04
> **FredSambo said:**
> It fails for me.  I have an old ATI Radeon 9200 and the Restricted Drivers Manager doesn't detect it.  I had to manually install the fglrx driver using the Edgy instructions [ located here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI").

Of course I should be ashamed of myself for using such an old and crappy video card.  :pThat's good to know, thank you.

---

### Post by jarocooke on 2007-06-04
> **mdz said:**
> Could someone confirm that System->Administration->Restricted Drivers Manager works fine in this configuration?  This is the officially supported method of installing the nvidia drivers, and is even simpler to access than third-party tools like Automatix.

I was just going to point out that the easiest way to install Nvidia drivers is to go the restricted drivers manager and just click the check box next to Nvidia Accelerated Graphics driver.  If I remember correctly from there on in everything is done for you (including updating xorg.conf), it even prompts you to restart the computer I think.

---

### Post by MetalMusicAddict on 2007-06-04
Nice Review.

Wow. Matt posted. :)

---

### Post by aysiu on 2007-06-04
> **jarocooke said:**
> I was just going to point out that the easiest way to install Nvidia drivers is to go the restricted drivers manager and just click the check box next to Nvidia Accelerated Graphics driver.  If I remember correctly from there on in everything is done for you (including updating xorg.conf), it even prompts you to restart the computer I think.
Yes. I have a step-by-step tutorial with screenshots:
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

### Post by esavato on 2007-06-04
I unfortunetley purchased a Dell E520 about two weeks before the announcement that Dell was going to support linux.  I was pleasantly surprised at how easily I was able to get my Nvidia 7300 LE up and running and getting my 20" monitor to display the 1680x1050 resolution.  I found that after I turned on the restricted drivers, I was able to use the Nvidia control panel and it found my monitor and it runs great.  Beryl also installed without any problems.

---

### Post by compiledkernel on 2007-06-04
For possible reasons why the Restricted Driver Application may fail, refer here and here.  The troubleshooting guides are fairly concise.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Most issues related to the use of the Restricted Drivers manager comes from what appears to be prior upgraded installs that used third party helper scripts to install their drivers. 

[quote=Nvidia page @ wiki.ubuntu.com]
(note: Restricted Devices Manager may not work properly on machines that have previously used 3rd party tools like envy to install previous drivers).[/quote]

---

### Post by FredSambo on 2007-06-04
> Most issues related to the use of the Restricted Drivers manager comes from what appears to be prior upgraded installs that used third party helper scripts to install their drivers.

For the record, I upgraded from Edgy, which was all set up with the fglrx Driver, I installed it using that exact HowTo in fact.  When I upgraded I just had to set it up again the way I did in Edgy.  I didn't use any 3rd party scripts for the Video Drivers, although I did use Automatix2 for other things, like Wine.

It was most likely something I did.  :p

---

### Post by timzak on 2007-06-04
> **mifi said:**
> Have a look at [http://ubuntuforums.org/showthread.php?t=461028]("http://ubuntuforums.org/showthread.php?t=461028").

It was suggested to add "reboot=b" to the end of the kernel line in /boot/grub/menu.lst.

I can confirm this workaround is working for me.

mifi

What exactly do you mean by "the end of the kernel line"...Can you copy that section of your menu.lst here so I make sure and put it in the right place?

Thanks.

---

### Post by mifi on 2007-06-05
> **FredSambo said:**
> It fails for me.  I have an old ATI Radeon 9200 and the Restricted Drivers Manager doesn't detect it.  I had to manually install the fglrx driver using the Edgy instructions [ located here](https://help.ubuntu.com/community/BinaryDriverHowto/ATI).
That is true. I have noticed that too for an ATI Radeon X1300 (not so old), but your earlier statement that "it fails more often than..." is perhaps a bit too bold.

By the way: I dropped my ATI and bought an nVidia GeForce 7300 for far less than $100. Both Ubuntu and I are happy now :D

m

---

### Post by nutz on 2007-06-05
> **mdz said:**
> Could someone confirm that System->Administration->Restricted Drivers Manager works fine in this configuration?  This is the officially supported method of installing the nvidia drivers, and is even simpler to access than third-party tools like Automatix.


I had no issues with the install or it running afterwards. This was on two separate systems but both with Nvidia GPU's...

One was a Quadro NVS 110M and the other is a desktop with a FX5200 256MB AGP. Both worked flawless right after the initial reboot...

The Quadro NVS 110M was from a Dell Latitude D620.

---

### Post by tseliot on 2007-06-05
> **FredSambo said:**
> It fails for me.  I have an old ATI Radeon 9200 and the Restricted Drivers Manager doesn't detect it.  I had to manually install the fglrx driver using the Edgy instructions [ located here](https://help.ubuntu.com/community/BinaryDriverHowto/ATI).
Restricted Drivers Manager doesn't install the driver for your card because the fglrx driver which supports your card (8.28.8) doesn't work on Feisty (which uses Xorg 7.2).

In this case it's not Restricted Drivers Manager's fault. You should use the open source driver.

---

### Post by jerhurwitz on 2007-06-28
I have a dell 2005fpw and a bfg geforce 7800gtoc video card. I used the restricted drivers manager to use the nvidia driver and then used "sudo nvidia-settings" to set my resolution too 1680X1040. This works fine and saves except for the fact that the restart button on the top toolbar along with the time and date stamp and the recycle bin on the bottom toolbar are not all the way over to the right hand side. Then instead are at a position they might be at if the right side of my monitor were to be chopped off so it wasn't widescreen.  Anyone know how to fix this?


Oh yea, i'm fairly new to ubuntu.

---

