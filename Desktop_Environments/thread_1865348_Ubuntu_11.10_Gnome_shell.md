---
title: "Ubuntu 11.10 Gnome shell"
date: 2011-10-20
forum: Desktop Environments
---

### Post by richard9090 on 2011-10-20
I just installed ubuntu 11.10. I switch to gnome shell, my display is tearing, flickering. I have made adjustments in ati catalyst control center but no improvement. I really want to use gnome instead of unity. Any suggestion to solve the problem. Thanks:(

---

### Post by waynefoutz on 2011-10-20
you need to remove the fglrx driver and install the open source Radeon driver. 

use this as a guide:
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")


You'll probably have to click on the link under "Removing the proprietary fglrx driver." Tha'ts what you need to do. Also ignore the part about adding the xorg-edgers PPA, because that doesn't work with Gnome-shell either. 

Read up on it first, but for me, these terminal commands and a reboot got me going:

```
sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*

  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
 
  sudo apt-get install xserver-xorg-video-ati

  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core

  sudo dpkg-reconfigure xserver-xorg
```


Once you get it running to your liking, to change it so you automatically boot up into gnome-shell instead of Unity run this command in the terminal:

```
sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-shell 
```

to undo that so it boots back into Unity by default:


```
sudo /usr/lib/lightdm/lightdm-set-defaults -s ubuntu
```


this will get gnome-shell working. The open source drivers are pretty good, but you will take a performance hit if you play 3d games like Urban Terror or Oil Rush. So if you don't care about that, the open source drivers are the way to go.

---

### Post by randywilharm on 2011-10-20
try this:

sudo dpkg-reconfigure -phigh xserver-xorg


Don't forget -phigh

---

### Post by waynefoutz on 2011-10-20
> **randywilharm said:**
> try this:

sudo dpkg-reconfigure -phigh xserver-xorg


Don't forget -phigh

When I did it, I forgot the phigh.....What did I miss when I forgot the phigh?

---

### Post by Zalbor on 2011-10-20
Does this mean that if I install Ubuntu 11.10 on my iMac (which doesn't work with the open-source driver and needs one downloaded from ATI/AMD's website) I won't be able to use gnome-shell??

---

### Post by t_ras on 2011-10-20
You will be able to use classic gnome (with much less custimability) but not the new gnome 3

---

### Post by Zalbor on 2011-10-20
Totally not what I wanted to hear...
Is there more information about what causes this somewhere? Why gnome-shell won't work with the driver?

EDIT: According to [this](http://joostruis.wordpress.com/2011/08/23/gnome-3-shell-and-fglrx-fixed-in-next-driver/), AMD said the issue would be fixed in the 11.9 version of the driver. I see that this driver is already out, at least for newer graphics cards.

---

### Post by richard9090 on 2011-10-20
waynefouts, thanks a lot. I followed your instructions, I could get gnome shell working well now, no more tearing, but some flickering still there on and off. Still have to try 3D games and see.:D

---

### Post by Zalbor on 2011-10-20
> **richard9090 said:**
> waynefouts, thanks a lot. I followed your instructions, I could get gnome shell working well now, no more tearing, but some flickering still there on and off. Still have to try 3D games and see.:D
If I were you, I'd see if my graphics card was supported by the driver I mentioned above and give it a try.
I can't test it yet myself though, because I'd have to reinstall and I'm waiting for Mint 12.

EDIT: It's a bit risky though, I've had trouble removing a driver from their website before.

---

### Post by Flymo on 2011-10-20
Thanks for the helpful info folks....

---

### Post by randywilharm on 2011-10-20
the -phigh flag selects default values for everything except resolution,
though some posters in this thread vary a little:

[http://ubuntuforums.org/showthread.php?t=346138]("http://ubuntuforums.org/showthread.php?t=346138")

Sorry I didn't mean to infer that you missed
anything, it was a suggestion to original poster.

---

### Post by waynefoutz on 2011-10-20
> **Zalbor said:**
> Totally not what I wanted to hear...
Is there more information about what causes this somewhere? Why gnome-shell won't work with the driver?

EDIT: According to [this](http://joostruis.wordpress.com/2011/08/23/gnome-3-shell-and-fglrx-fixed-in-next-driver/), AMD said the issue would be fixed in the 11.9 version of the driver. I see that this driver is already out, at least for newer graphics cards.

I tried the 11.9 driver, I have the Mobility Radeon 4250, and got no improvement. It was still garbled with tearing. Gome-shell runs beautifully with the open source driver, I'm not getting any flickering. For 99% of the stuff I do, the open source Radeon is adequate. You will take a performance hit with 3d games though. For instance, Urban Terror on my laptop runs around 90-95 frames per second with the fglrx (proprietary) driver installed. With the open source Radeon driver, the framerate drops to around 45 fps, which is still playable. 

The bottom line is, if that kind of stuff is important to you, stick with the fglrx driver and Unity. You are by all means welcome to try Catalyst 11.9, if it works, let me know. I'm just saying that it didn't work for me.

---

### Post by richard9090 on 2011-10-20
Yes,fglrx driver works well with Unity in my computer. There is no tearing, flickering, 3d game working, well, after trying gnome 3.2 i think i am going to switch back to unity. Will keep you informed

---

### Post by waynefoutz on 2011-10-21
> **richard9090 said:**
> Yes,fglrx driver works well with Unity in my computer. There is no tearing, flickering, 3d game working, well, after trying gnome 3.2 i think i am going to switch back to unity. Will keep you informed

I prefer gnome-shell, at least for the moment. The gaming issue isn't that important to me.

---

### Post by richard9090 on 2011-10-22
after trying both unity and gnome, i am in two mind: which desktop to use: unity or gnome. Both are good, both have their own plus and minus points. Are there features which make one desktop better than the other, or is it only a matter of personal taste?

---

### Post by waynefoutz on 2011-10-23
> **richard9090 said:**
> after trying both unity and gnome, i am in two mind: which desktop to use: unity or gnome. Both are good, both have their own plus and minus points. Are there features which make one desktop better than the other, or is it only a matter of personal taste?

it's personal taste. They both do and accomplish the same things, just with a different layout. They both very well could be a fad that runs it's course. I'm all ready starting to miss the simplicity of Gnome2 and I can eventually see myself going to the Xfce desktop before long.

---

### Post by richard9090 on 2011-10-30
right oh! i just dropped ubuntu 11.10 to go to...Mint 11. I got everything done with much more ease. Still I have the problem of setting higher resolution to my monitor [URL="http://ubuntuforums.org/showthread.php?t=1870986"]

---

