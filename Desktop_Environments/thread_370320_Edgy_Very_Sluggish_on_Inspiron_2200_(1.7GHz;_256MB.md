---
title: "Edgy Very Sluggish on Inspiron 2200 (1.7GHz; 256MB RAM)"
date: 2007-02-25
forum: Desktop Environments
---

### Post by SendDerek on 2007-02-25
Hello All!

I was just curious as to if I did something wrong while installing Edgy Eft on an older laptop.  Is 6.10 too "edgy"?  Should I use 6.06 instead?  Would there really be much of a difference.  Basically, the biggest problem is that it's a little sluggish.  For example, while listening to music on Amarok, the music will skip and the system will totally slow down if I try and open up firefox or even a folder to browse through pictures.  I like to have a few programs open at time, namely Amarok, Firefox, F-Spot, and overall nautilus browsing.  Make sense?

Here are the system specs:
# Intel Pentium M 735 (1.7GHz) Processor
# 256MB PC2700 DDR Memory
# 40GB 4200rpm Hard Drive
# 24x CD-RW/DVD Combo Drive
# 14.1" XGA LCD and Intel GMA 900 Integrated Graphics with 128MB Shared Memory
# AC'97 Audio
# v.92 56Kbps Modem, 10/100 Ethernet, 802.11g Wireless

256MB is all that shows up in the BIOS, and I'm aware that the video memory is shared so there is even less than 256MB being dedicated to system processes.

Is there something I did wrong during the install?  I believe the video card and everything was automatically picked up...  It took some work with the wireless, but otherwise everything else installed smoothly.  

Are there some packages I missed that would speed things along?  Is there a program that I can remove to make it faster (like ubuntu-desktop for example)?  Is the only other option to go along with Dapper? 

Anyways, just a bunch of questions all at once... sorry about that, but I would like to know of other's experience on an older laptop.

Thanks in advance!
Derek

---

### Post by iamhugeinjapan on 2007-02-25
You may have better performance running the Xfce environment, which is light and GTK based like GNOME.

```
sudo aptitude install xubuntu-desktop
```

But if you're wanting to run things like Amarok you'll still be loading the KDE libs into memory which will slow things down too.

---

### Post by SendDerek on 2007-03-07
Turns out that the computer was pretty sluggish in windows as well.  This was a laptop I was doing for a friend, and after I had windows installed, he wanted to keep it that way until he gets a new laptop to throw ubuntu onto.  Thanks for the help.

---

### Post by H.E. Pennypacker on 2007-05-06
256MB is hardly impressive.  Upgrading your RAM to at least 1GB would be very helpful.  Did the trick on my Inspiron 2200.

---

