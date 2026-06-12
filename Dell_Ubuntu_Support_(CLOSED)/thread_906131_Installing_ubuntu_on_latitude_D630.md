---
title: "Installing ubuntu on latitude D630"
date: 2008-08-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jamedadi on 2008-08-31
Hi 
I am very new to linux and I need some help. I have a latitude D630 which has a Intel(R) Core (TM) 2 Duo processors. Know I have tow questions :

1- what release of ubuntu I have to install? i386 version or 64x version?
2- Can anyone please get me a clear checklist for installing ubuntu 8.04? I have already installed Windows XP on drive C, and I want to install ubuntu in other drive (for example D)

Thanks a lot

---

### Post by elishock2420 on 2008-09-01
I have a Latitude D630 running Ubuntu 8.04.  What type of video and wireless card do you have?  Do you have an space set aside for ubuntu?
Installation is pretty straight forward.  If you have an nVidia card it can sometimes be tricky, install envy from add remove programs and run the nvidia install it makes setting up the proper drivers easy.  If you have more questions I can try to answer them.

---

### Post by linux_tech on 2008-09-01
This guide explains the best how to install ubuntu 8.04 with XP already installed to dual boot.  [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)
If you have a core 2 then you should download the 64 bit version
[http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)

---

### Post by Wolfhere on 2008-09-05
I have a D620. I added another drive in my bay. I then used the wubi.exe to install to my 'addon' partition. Dual boot works great..and I agree whole heartedly...use EnvyNG (loaded through synaptic manager). Problems with video through the Dock though. Release 8.10 is just around the corner and is supposed to have some fixes for the Dell Dock included.

---

### Post by waffen on 2008-10-01
are you sure? because I just installed Ubuntu 32 bits and works fine... whats the difference?

---

### Post by sbrbot on 2008-10-05
Dell Inspirion D630 is 32-bit machine regardles of two CPU (dual core CPU). You should install Ubuntu 8.04 and it works perfectly well in this machine. Ubuntu will detect all hardware by default - that includes Intel PRO/Wireless 3945 wireless card, firewire connection, Nvidia graphic card in full 1440x900 resolution, etc. The only thing that is not detected by default is fingerprint reader but it can be setup easily using ThinkFinger driver that can be found in official hardy repository and work on linux as well.

---

### Post by waffen on 2008-10-05
No, the Latitude D630 is a Core 2 Duo (64 b) so I must be install the Ubuntu 64 version...

---

### Post by Tweak42 on 2008-11-04
Core2 cpus can use 32 or 64bit.

I have a Latitude D630 and just took the leap and wiped my working 32bit 8.04 install partition of my hard drive (also have XP+Vista dual booting) and installed 64bit 8.10 ibex.  

I went to 64bit because I upgraded to 4gb of memory just now and there appears very few reasons not to go 64bit. (see the 64bit forum for more current info)

_Fixes I had to find:_
I did not need to use ENVY for video drivers this time.  I used the "Hardware Drivers" app and installed the Nvidia 173 (177 has bug keeping fan running 100%)
Needed to install gsynaptics and get it working as detailed here:[https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)

I'm still working on getting the fingerprint reader working again, but pretty happy that system working pretty well as the video drivers were a pain to get working just right last time.

---

### Post by waffen on 2008-11-04
uhm...good tip about the cooler, I dont listen any because I use my laptop over a cooler base (3 funs running)...

I use here both Ubuntu:first 32bits and right now 64, and I see 64 is more fast. I could use all my programs: Java, Firefox, Eclipse, Skype, etc. some config problems but the life is not easy :p

Change my Nvidia dirver to 173 and in the next hours I can test if the cooler run everytime.

---

### Post by Mega_Mike on 2008-11-05
I have a latitude D830 and installing 8.10 Intrepid was pretty simple with only a hiccup with getting the front microphone/audio capture to work with skype.

[LIST]
[*]Step 1:  Run gnome-volume-control from a terminal, select preferences and make 'capture' is checked.  Then go back to the main control panel and make sure the volume is turned up on 'capture'.  Lastly, go to 'options' and make sure 'front mic' is selected for both pulldowns.
[*]Step 2: Open gnome-control panel and select sound preferences.  Under capture select PulseAduio Sound Server.  Also make sure you 'Default mixer tracks' is set to HDA-Intel (alsa mixer)
[/LIST]

Lastly,
  this is an old article, but its tweaks still old up today, especially for a Dell laptop.  I have been using it to keep my system zippy since Ubuntu 7.04.

[http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml)

Looking at the article for installing gsynaptics (for configuring the touchpad) that was mentioned by a previous poster is a huge help.

Plus installing the medibuntu repositories to install the 'non-free codecs' and skype make the multimedia experience on Ubuntu complete.
[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by waffen on 2008-11-05
My mic not work, when I go to gnome-sound-recorder I allways see my mic disable, I make able, close the window, reopen and the mic is disable allways.

Another: when I open the gnome-volume-control I click Recorder and the counter start and move on and never stop.... any idea??

---

### Post by undoIT on 2009-01-04
> **waffen said:**
> My mic not work, when I go to gnome-sound-recorder I allways see my mic disable, I make able, close the window, reopen and the mic is disable allways.

Another: when I open the gnome-volume-control I click Recorder and the counter start and move on and never stop.... any idea??

Internal mic is not working for me either on the Latitude D830. I don't see any options with a pull down for "front mic".

---

### Post by undoIT on 2009-01-04
Okay. You need to also enable input source in volume control preferences to get at the internal mic. Now it is working.

---

