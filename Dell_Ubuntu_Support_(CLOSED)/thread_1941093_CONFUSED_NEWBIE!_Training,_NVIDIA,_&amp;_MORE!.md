---
title: "CONFUSED NEWBIE! Training, NVIDIA, &amp; MORE!"
date: 2012-03-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by GpD79 on 2012-03-15
Hi All,

I JUST installed Ubuntu 11.10 64 bit along side Win7 a few hours ago.  Most things seem to be working okay.  I'm still getting used to everything, but there are some issues that I cannot seem to figure out just yet.  Please allow me to list them below.

[LIST=1]
[*]Ubuntu/Linux is so new to me,I really have no idea what I'm doing.  I've been resorting to going to youtube to try and figure how to use it.  Is there a better way to learn the basics?  Maybe instructional videos?
[*]I've seen video's that show that Ubuntu automatically detects additional drivers; however, when I scan for those drivers, it says that no proprietary drivers are in use on this system.  When I watched the videos though, they almost always show how NVIDIA is detected on their system.  Since it didn't detect it, I went to NVIDIA's website and downloaded the correct driver for Linux.  Unfortunately, I have no idea how what to do with it now that I've downloaded it, even through there were instructions!  This causes me to ask 4 questions.
[LIST=1]
[*]How would I install the driver.  Here is the websites instructions:

[I]"Once you have downloaded the driver, change to the directory  containing  the driver package and install the driver by running, as root, sh  ./NVIDIA-Linux-x86_64-295.20.run

  One of the last  installation steps will offer to update your X  configuration file. Either  accept that offer, edit your X configuration  file manually so that the NVIDIA X  driver will be used, or run  nvidia-xconfig"[/I] 

I have no idea what any of that means!!!  The instructions can be found here:
[http://www.nvidia.com/object/linux-display-amd64-295.20-driver.html](http://www.nvidia.com/object/linux-display-amd64-295.20-driver.html)
[*]Is NVIDIA already supported in Ubuntu so that it does not need the additional driver?
[*]How would I know if NVIDIA is actually working or not?
[*]When I search for NVIDIA in the dash, I do find NVIDIA X Server Settings, but when I click on that I get the following error message: "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."  I have no idea what that means.
[/LIST]
 
[*]When I used Win7, I was able to use an HDMI cable to connect my laptop to my TV and watch online content on the big screen.  For some reason, when I plug the cables in, nothing happens.  I have a feeling this is somehow connected to NVIDIA b/c whenever I did that on Win7, an NVIDIA thing would open and do it's thing.
[/LIST]


I have more concerns , but these are my biggest concerns right now.  Any help ANYONE can provide would be really grateful.  Ugh... I HATE BEING A NEWBIE!  



Frustrated in NH,
Graz

---

### Post by VH-BIL on 2012-03-15
1. You can learn from all types of websites including youtube, there is sites that will offer training that you pay for like [http://learnubuntu.org/](http://learnubuntu.org/) and also receive support from the community of forums like this. The main thin to learn is how to install software and then access the installed software.

2. Make sure you have updated the repository before checking for drivers. You can do this with the following command in the Terminal:```
sudo apt-get update
```The load the Additional drivers dialog and activate the recommended (Current) driver. It is better to use the driver in the repository or you will have to recompile it everytime you get a kernel update.

3. I am pretty sure HDMI will work when your nVidia driver is installed.

Let me know how you go :)

---

### Post by GpD79 on 2012-03-15
Hi There,

Thanks for your help so far!  I went ahead and updated [FONT=Verdana]the repository by going to the terminal and entering sudo apt-get update.  (Thank GOODNESS you said terminal because I was able to find that in the dash search.  Otherwise, I would of been more stuck than I am now.)  After that, I just typed exit to close it out.  I hope I did that right.

Now I'm supposed to load the additional drives dialog?[/FONT]  I'm assuming that's the thing I found in System Settings.  I double clicked that again, it searched for additonal drivers, but unfortunately it again said "No proprietary drivers are in use on this system."  Did I do something wrong?

Graz

---

### Post by VH-BIL on 2012-03-15
I am assuming that when it said no additional drivers are in use in this system that it meant you have not activated one yet. There should be one or two in the list you can click and activate.

When you activate one it will be downloaded and installed for you.

Let me know how you go and I will be glad to help you fix this if it is not resolved.

---

### Post by AgentZ86 on 2012-03-15
There should be one shown in the window that you can select which says either (recommended current) or latest current

If you have nothing to select then jockey is the program that should be detecting this

What video card are you using ?

---

### Post by GpD79 on 2012-03-15
Hi again,

Thanks so far for your help.  To answer any questions about  my computer, here is the rundown from the manufacturer.
Here is a description of the computer:

[SIZE=1]1 2nd generation Intel Core i7-2630QM processor 2.00 GHz with Turbo Boost 2.0 up to 2.90 GHz
1 6GB,DDR3,2 DIMM
1 Backlit Internal Keyboard - English
1 15.6HD TLF WLED LCD L50xX
1 NVIDIA GeForce GT 525M 1GB graphics with Optimus
1 750GB 7200 RPM SATA Hard Drive
1 Genuine Windows 7 Home Premium 64 bit Service Pack 1, English, No Media
1 Tray Load Blu-ray Triple Writer (reads and writes CDs, DVDs, BDs)
1 JBL 2.1 Speakers with Waves Maxx Audio 3
1 Intel Centrino Wireless-N 1030 and Bluetooth 3.0
1 90 WHr 9-cell Lithium Ion Primary Battery
1 Microsoft Office 2010 Home and Student, English
1 2.0MP HD webcam with single digital mic (H.264)
1 Mini DisplayPort (1),
2 USB 3.0
1 USB 2.0 (eSATA/powershare combo)
1 Integrated network connector 10/100/1000 LAN (RJ45)
1 HDMI 1.4
1 Audio jacks: headphone (2 total) with SPID/F support (1), 1 Mic-in
1 9-in-1 media card reader Supporting SD, SDIO, SDXC, SDHC, MS, MS Pro, MMC, MSXC, xD
[/SIZE]
I'm kind of confused as to whether I am doing it correctly.  JUST to make sure, I'm going to show you pictures of what I've done.

Step 1.  Clicked on Additional Drivers in System Settings


Step 2: Watched it do it's scanning thing:


Step 3:  Looked to see the results of it, but there were none there.




What am I doing wrong?

---

### Post by AgentZ86 on 2012-03-15
Check this out

Sounds like you need bumblebee

Read this forum and the links there about it

[http://www.linuxquestions.org/questions/ubuntu-63/should-i-install-nvidia-geforce-gt-525m-driver-on-ubuntu-11-10-a-924760/](http://www.linuxquestions.org/questions/ubuntu-63/should-i-install-nvidia-geforce-gt-525m-driver-on-ubuntu-11-10-a-924760/)

Hope this helps

---

### Post by GpD79 on 2012-03-15
Thanks AgentZ86 for the suggestion; however, I don't understand how to do what it's asking.  :-(  I'm just really frustrated right now.

---

### Post by veroslav on 2012-03-16
Hi,

I have exactly the same graphics card and I managed to configure it with bumblebee by following the instructions found here (I hope it helps):

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by GpD79 on 2012-03-16
Hi veroslav,

Thanks for the recommendation.  I followed the instructions from the wiki Bumblebee page.  But I do not think I was successful.  I took pictures of what I did just to make sure I did it right.  Do I need to download bumble bee from somewhere first to make it work?

---

### Post by GpD79 on 2012-03-19
I notice that whenever I try to add the repository for bumblebee in the terminal, I get the following error message.

**pycurl**.**error**: (**35**, '**gnutls_handshake**() failed: A TLS packet with   unexpected length was received.')

Does anyone know what that means and how to fix it?  I think that's what's stopping me from getting this fixed.

---

### Post by VH-BIL on 2012-03-19
Have you tried adding other repos?

---

### Post by GpD79 on 2012-03-19
I'm guessing no.  But I'm not sure.  I'm pretty new to this.

---

### Post by GpD79 on 2012-04-07
SUCCESS!  I am visiting my family in back home in New Jersey and I tried installing bumblebee.  IT WORKED!  I think maybe the school network that I use interfered with installing it.  I have no clue.  Now that it's installed, I figured I could connect my computer to m TV and watch content.  Unfortunately, it's not working.   How do I make this work?

---

