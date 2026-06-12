---
title: "[SOLVED] Upgrading Inspirion laptop"
date: 2008-05-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RetiredInMaine on 2008-05-07
I have an Inspirion 1420 with ubuntu 7.04 loaded.  I have 7.10 on my desktop and would like to stay in sync. I ran the live 7.10 cd on the laptop. The wireless card seemed to find my router, and even seemed to connect. But I could not get to the internet. This makes me very leary about upgrading.

Also, if I install from the live cd will I get an upgrade or will it be a total reinstall and I loose everything in my home directory? If yes, is there any way to upgrade as opposed to reinstalling?

If anyone has any experience with upgrading Dell systems or insight into this I would like to hear from you.

---

### Post by shae on 2008-05-07
I am using a Dell Inspiron 1420N with Ubuntu 7.10.  I have Intel Wireless Pro 3945.  What wireless card do you have?  Have you considered using the Dell ISOs avaliable from Dell: [Clicky]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10")

---

### Post by joker2of5 on 2008-05-07
I have a Dell 1420n that came with 7.04 pre-installed.  Right after I got it I  upgraded to 7.10 with the software update utility.  I had quite a few problems as a result of the upgrade.  

After Dell released the ISO image for 7.10, that is customized for this computer, I downloaded that and installed it.  I have not had any problems with this computer since.  Aside from a minor issue with the wireless utility freezing up occasionally.

The  installation from the CD is a complete reinstall, so remember to back everything up first.

---

### Post by caro on 2008-05-07
I have a Dell Inspiron 1505 that was preloaded with Feisty.  I used the update feature to upgrade to both Gutsy and Hardy with no problems.

---

### Post by RetiredInMaine on 2008-05-08
First, thanks to all of you for responding.

SHAE: I followed the link you provided. It now talks about upgrading to 8.04 rather than 7.10. I'm not sure I want to go to 8.04 just yet, I have read too many horror tales from those who have already gone to 8.04.

joker2of5: you mentioned that Dell had released an ISO image for 7.10. I went to the Dell web site and did a search for "ubuntu 7.10 image" (any of the words), also for "ubuntu iso image", (without the quotes around the words of course)  and did not find any mention of any ISO image. Can you post the url? I would like to give that a try.

---

### Post by notwen on 2008-05-08
[Here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Dell_OS_Reinstallation_7.10_DVD_ISO") are the custom Gutsy images available from Dell.  Be sure to download the appropriate iso for your machine, one iso is for the Intel X3100 while the other is for nVidia 8400M GS.  

Did you order this laptop w/ Ubuntu already installed or did you order a machine w/ Vista?  I only ask because the Vista machine has options to customize your machine w/ hardware that may/may not be compatible w/ Ubuntu.  These custom Gutsy images were made for very specific hardware, specifically the N-Series models that came pre-installed w/ Ubuntu.  You could compare your hardware specs to the 1420n at [http://dell.com/open](http://dell.com/open) to verify your hardware is compatible.

I also have a Inspiron 1420n and am using the custom Gutsy image until Dell releases their custom Hardy images.  Post if you have any questions and/or issues.  Best of luck.  =]

---

### Post by RetiredInMaine on 2008-05-08
notwen: thanks for the info. Color me naive, I did not know that all 1420N's were not the same. I went to the Device manger to see what I had but I'm still confused. The only graphics I see listed is the Mobile Integrated Graphics Controller. I have never heard of this so I don't have a clue how to handle it. I ordered my system with ubuntu pre-installed as I do not use any MS software. My desktop is strictly Linux. After I post this I will follow your link and see what I find. I'll post my results.

---

### Post by psycosmyth on 2008-05-08
Not sure about your problem. I have a Insp 1200 and it runs whatever I throw at it, right now I have Kiwi which is Ubuntu with a few tweaks. I have no issues with Hardy but I am using an pcmcia card and not an internal.
You might want to stick with what works or you can dive in with a re-install. I have had 40+ distros on this 3 year-old box!

---

### Post by notwen on 2008-05-08
> **RetiredInMaine said:**
> notwen: thanks for the info. Color me naive, I did not know that all 1420N's were not the same. I went to the Device manger to see what I had but I'm still confused. The only graphics I see listed is the Mobile Integrated Graphics Controller. I have never heard of this so I don't have a clue how to handle it. I ordered my system with ubuntu pre-installed as I do not use any MS software. My desktop is strictly Linux. After I post this I will follow your link and see what I find. I'll post my results.

If you got your laptop w/ Ubuntu 7.04 pre-installed it is very likely you have the Intel X3100 graphic chipset.  They did not begin to offer the nVidia chipset until the machines w/ Gutsy pre-installed.  Since I ordered mine as soon as they began offering the N-Series, I am also using th X3100 chipset.  Let's verify just to be safe.  Open up a terminal and type in the following command and post back the output here:

```
lspci
```

---

### Post by RetiredInMaine on 2008-05-09
notwen: You are right I have the intel video board. Thanks. I downloaded the proper iso image. I'll post my results after I try it out.

---

### Post by RetiredInMaine on 2008-05-13
I tried several times to run the iso image I burned from Dell. Got a bazillion error messages. Gave up for now.

---

### Post by LMP900 on 2008-05-13
> **RetiredInMaine said:**
> I tried several times to run the iso image I burned from Dell. Got a bazillion error messages. Gave up for now.

That's strange. What error messages are you getting?

I believe I have the same notebook as you (Inspiron 1420n w/ Intel X3100 preloaded with Ubuntu 7.04). The Dell custom 7.10 image worked without any issues for me. Which image (filename) did you download and how did you burn it into a DVD?

Also, if you're interested, Ubuntu 8.04 works without issues on the 1420n as well (at least not any that I have come across). Sound, internet connection, and even Compiz - the three things I thought I would have problems with, all work flawlessly from the start.

---

### Post by notwen on 2008-05-15
After downloading Dell's custom image did you check the md5sum?  If that came up w/o any issues, only thing I can think of is a bad burn, burn at 4x or slower.  Post back and give us a update on your situation.  =]

---

### Post by RetiredInMaine on 2008-09-02
Sorry it took me so long to update this thread. I installed the upgrade from 7.04 to 7.10 yesterday but alas I did not use the custom ISO, used the download from the repositories. Big mistake. 

When I boot I go into console mode. After logging in and running the startx command I get the following error message:

Fetal Server error: No Screen found
XIO fatal IO error 104 (connection reset by peer on X server "0.0" after 0 requests (0 known processed) with 0 events remaining

When I shut down I see a message that gdm is shutting down, so it is running, just can't find the screen.

My question: Is there a fix for this or do I have to reinstall? And if I reinstall what version should I install? I've been reading a lot of horror stories about 8.04.

BTW, I'm not really concerned about data loss, everything on my laptop is also on my desktop and that is backed up on a regular basis.

Not sure if anyone is still subscribed to this thread. If I don't get a reply I'll just have to bite the bullet and go for a reinstall. :confused:

---

### Post by RetiredInMaine on 2008-09-03
OK I reinstalled from a normal, ie non Dell iso and all works fine now Thanks to all of you for posting

---

### Post by blueb73 on 2009-04-03
I am also looking to upgrade.  I have the 1505, and want to go from 7.04 to 7.10 Then to 8.04).

I noticed dell doesnt have an ISO for my model [http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Dell_OS_Reinstallation_7.10_DVD_ISO](http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Dell_OS_Reinstallation_7.10_DVD_ISO)

should I try and use the one from ubunut?  [http://releases.ubuntu.com/gutsy/](http://releases.ubuntu.com/gutsy/)

thanks!

---

