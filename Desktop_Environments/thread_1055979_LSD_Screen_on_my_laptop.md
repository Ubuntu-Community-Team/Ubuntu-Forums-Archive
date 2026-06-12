---
title: "LSD Screen on my laptop"
date: 2009-01-31
forum: Desktop Environments
---

### Post by itarato on 2009-01-31
Hi,

I tried to install Ubuntu 8.10, but when X11 started, colors on the screen started to turn some kind of LSD style. Somewhere it could be seen vibration. My laptop is an Asus A6U model (with embedded SIS M760GX ). After I tried Fedora 10 and LinuxMint 6, but got the same problem.
(Just see what about the older versions, that were worked fine.)

I googled it, but cant find anything.

Its because the kernel version? Or my laptop is not compatible? How can I solve this?

Thank you in anticipation

---

### Post by skern03 on 2009-01-31
> **itarato said:**
> Hi,

I tried to install Ubuntu 8.10, but when X11 started, colors on the screen started to turn some kind of LSD style. Somewhere it could be seen vibration. My laptop is an Asus A6U model (with embedded SIS M760GX ). After I tried Fedora 10 and LinuxMint 6, but got the same problem.
(Just see what about the older versions, that were worked fine.)

I googled it, but cant find anything.

Its because the kernel version? Or my laptop is not compatible? How can I solve this?

Thank you in anticipation

Can you read the screen at all? In any event, you want to make sure you have the SiS display drivers installed (X.Org X server). 

If you can read the screen, you can check in Synaptic Package Manager (search for SiS), if it's installed, the checkbox will be solid. If it isn't installed, then install it.

If you can't read the screen, during boot, you should see at least two choices, the first is the most recent kernel, the second is a repair option. Choose the second. You'll get a menu with several options, one of which is root terminal. Once you're logged in as root, you can run this to install the drivers:
```
apt-get install x-server-xorg-video-sis
```

That MAY help. If it doesn't, search this forum for your specific laptop name and/or the SiS module name.

---

### Post by itarato on 2009-01-31
Thanks for the quick reply.
I checked, and xserver-xorg-video-sis (1:0.10.0-1build2) was already installed. 

I download 2 driver from SiS site, but it did't work, because it (and me as well) couldnt find any XF86Config file.

So I dont know whats next... I try Ubuntu Japerty alpha.

Thanks,

---

### Post by skern03 on 2009-01-31
> **itarato said:**
> Thanks for the quick reply.
I checked, and xserver-xorg-video-sis (1:0.10.0-1build2) was already installed. 

I download 2 driver from SiS site, but it did't work, because it (and me as well) couldnt find any XF86Config file.

So I dont know whats next... I try Ubuntu Japerty alpha.

Thanks,

A different version of Ubuntu isn't likely to help, and neither will another distro - you already tried several, right? The problem is that Linux drivers aren't playing nice with your SiS integrated graphics chipset.

Here's what I suggest - click the URL below. It's a link to a sticky post in the Multi-Media forum, Comprehensive multi-media and video how to:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
I've used both sticky posts on that forum, and they are very useful.

---

### Post by itarato on 2009-02-01
Thanks for the page. I'll read it in a minute.
Yesterday I've got a suggestion to change Monitor driver from sis to vesa. Its solved the color and vibration problem, but messed up the other setup (eg resulution). And strangely it freezed on every bid i tried to modify the xorg.conf.

Now i'll gonna read the article, thanks again!

---

### Post by itarato on 2009-02-01
Nothing:( All day I take this, but nothing. Tried to replace sis driver to that one in hardy. Tried to give in xorg.conf the hsync and vsync. Tried to update all system.
I'm desperate:)

It has to be ready by tomorrow...

---

### Post by skern03 on 2009-02-01
> **itarato said:**
> Nothing:( All day I take this, but nothing. Tried to replace sis driver to that one in hardy. Tried to give in xorg.conf the hsync and vsync. Tried to update all system.
I'm desperate:)

It has to be ready by tomorrow...

Wish I could be of more help...

Try looking here:
[http://www.linlap.com/wiki/asus+a6u](http://www.linlap.com/wiki/asus+a6u)

They have some tips on how to get the A6U working with Linux.

---

### Post by DavidTangye on 2009-04-12
> **skern03 said:**
> A different version of Ubuntu isn't likely to help, and neither will another distroNot true. I have the same problem on the same model of Asus laptop. X worked fine with Hardy, but not Intrepid. It also works fine with Puppy 2.17.
> **skern03 said:**
> The problem is that Linux drivers aren't playing nice with your SiS integrated graphics chipset.Perhaps the problem is with the specific SIS driver as currently packaged for Intrepid. Perhaps its a particular compiler option that was chosen.

---

### Post by DavidTangye on 2009-05-16
FYI: See my post in [http://ubuntuforums.org/showthread.php?t=1055979#post7112777](http://ubuntuforums.org/showthread.php?t=1055979#post7112777), where I show the xorg.conf file that fixes the problem. It shows the sis driver and all its possible options. Perhaps one of them would fix the problem. However, as also shown, I switched out the sis driver and switched in the vesa driver.

Edit: Sorry I think that should have been [http://ubuntuforums.org/showthread.php?p=7293439](http://ubuntuforums.org/showthread.php?p=7293439)

---

