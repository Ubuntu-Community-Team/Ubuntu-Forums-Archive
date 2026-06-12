---
title: "boot from Ubuntu 8.10 live CD results in black screen"
date: 2008-12-11
forum: Desktop Environments
---

### Post by rafttrip on 2008-12-11
I am trying to install Ubuntu 8.10 from a live CD. when I boot I get the menu to boot to live Ubuntu. I select this and then the splash screen shows the Ubuntu logo and the brown bar across the screen. than I hear the drum role but I get a black screen.

I have an ATI video card on this machine.
I tried to use the safe graphics mode...same result.
I have had Ubuntu 8.04 working before although I seem to recall having this problem with 7.10 as well.

I did some googleing but could not find anything that involved a live CD.

I would like to install Ubuntu but not sure how I can do that if I can't even boot to Live CD.

Thanks in advance for any help.

---

### Post by albinootje on 2008-12-11
Please post the specifications of your video-card (and machine).
You might want to consider using the text-mode installation and then later fix the graphics problems.

---

### Post by rafttrip on 2008-12-11
I have a Gigabyte Radeon x1300 pro video card

I'm a bit scared of text install but I'm willing to give it a try... isthere a How To or some advice you can give me?

Thanks for the speedy reply by the way

---

### Post by albinootje on 2008-12-11
You're welcome.

Download the alternate cdrom image here :
[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

Here's someone with a quite similar problem, with a solution :
[https://answers.launchpad.net/ubuntu/+question/28945](https://answers.launchpad.net/ubuntu/+question/28945)

-- possible solution ----------------------------
Try to select the graphic card via name:
1. fglrx
2. ati
3. radeon

If none of them are working you can install the package xserver-xorg-video-radeonhd. Then try to select radeonhd as graphic driver. (The radeonhd driver in the package repository is old, may be too old for your card).
----------------------------------

Looks like your safest bet is to go for Hardy Heron.
The text-base install is really not that more difficult than the graphic installation. Just as with the graphical installation you need to take some more time to look at the partitioning step.
GL!

---

### Post by Vantrax on 2008-12-12
Ill second the recommendation to try the alternate cd or text only install.

If after install you have no video there is a bigger problem.

---

### Post by rafttrip on 2008-12-12
downloading the alternat CD is not a good option for me. I live in a remote community in the Australian Outback and our monthly download limit is 1.2 GB and there are other people using this connection. Imailk ordered the Live CD before I realised I needed the Alternat CD... I will know for next time. I would like to do it another way I think the text instaler it will be.

thanks

---

### Post by quadproc on 2010-02-27
I suspect that your system is actually booting but that the X windows server is not starting.  I had similar problems at first, in my case, it was due to having two ATI video boards because the X server couldn't figure out which one was the primary card and so the server just gave up and would not run.  To get around this, I modified my /etc/X11/xorg.conf file to add a BusID entry to the first card; that prevented confusion in the X server.

Another thing that you might try is changing the video card driver selection in the xorg.conf file.  If you can stand a low performance driver with very few options then you could use "vesa", at least temporarily.  Once you get your system running again then you could change the driver to "ati" or "fglrx".

When I changed from Ubuntu 8.10 to 9.04 I found that my system went stone dead at the same point that you are getting to.  I spent two very long days trying different things to get it working; as I recall, one key element was changing "fglrx" to "vesa" just so that I could troubleshoot with the software tools that I am used to.  The presence of fglrx was somehow involved in the failure to display video.  I finally reinstalled fglrx after everything else was squared away.

Good luck!

quadproc

---

