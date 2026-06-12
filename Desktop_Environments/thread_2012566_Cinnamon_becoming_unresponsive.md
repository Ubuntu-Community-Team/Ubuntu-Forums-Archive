---
title: "Cinnamon becoming unresponsive"
date: 2012-06-29
forum: Desktop Environments
---

### Post by rattata on 2012-06-29
Hi, I hope I'm posting this in the right place!

I'm using Ubuntu 12.04 and have the following desktop environments installed on my system: Unity, Gnome Shell and Cinnamon. My favourite by far is Cinnamon, but I'm experiencing a very annoying problem with it.

After a while of using my computer, the system will suddenly becoming unresponsive. It's not a full freeze, as I can still move my mouse and the cursor will change depending on what item it's hovering over (still shows text cursor over text, hand over links, etc.). Nothing I do can unfreeze it, as I cannot launch the terminal, close windows, use the restart Cinnamon applet, etc. The only thing I can do is shut my computer down using the button.

After it's happened once, it starts happening more and more often. For example, the system will work perfectly for hours, then freeze. Once I've restarted, it will happen after maybe 20 minutes. Freeze, restart. Ten minutes. It's never the same time, however.

I do not have this problem with any other desktop environment and I see no reason for it to happen with Cinnamon.

It does not seem to matter what I'm doing, as it will happen when I have no apps open, when I have Firefox open, when I have Chromium open, when I have LibreOffice open, etc.

Any help with this problem would be appreciated!

My laptop is a Toshiba Satellite C670. I cannot test Cinnamon on another computer in the house for this problem, unfortunately.

---

### Post by kd4dii on 2012-06-29
Hello
     I can't help much with Cinnamon as I have only used it on a live cd boot and was not impressed.  I have used the Mate fork of Gnome and found it very good.  I have used it in 11.1 and 12.04 as well as Linux Mint.
     If you want to give it a shot the instructions below are for 12.04.



Add the repo to /etc/apt/sources.list via the following command:

sudo add-apt-repository "deb [http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu) precise main"

or using a text editor of your choice add the following mirror to /etc/apt/sources.list:

deb [http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu) precise main

MATE Installation (both Oneiric/Precise)

Then run the following command to update your repositories and install MATE:

sudo apt-get update
sudo apt-get install mate-archive-keyring
sudo apt-get update
# this install base packages

sudo apt-get install mate-core
# this install more packages

sudo apt-get install mate-desktop-environment

You can select Mate at the login prompt.  Hope this helps you,

Bob

---

### Post by rattata on 2012-06-29
Thanks, Bob, but I've taken a look at Mate and I'm not really interested in using it. If I have to choose another desktop environment, it would be Unity. The thing I like about Cinnamon is the way it manages windows, the kinds of applets it has, how compact it is, the menu, etc. I've used Gnome 2 before and wasn't impressed. Cinnamon is just the perfect DE for me, as it suits the way I work so well. ^^

Thank you for the advice, though. =) I'd just rather have Cinnamon work properly for me.


Through some searching, I haven't found any mention of the problem I'm having. Maybe I'm not looking hard enough, I don't know. I have no idea if this is a common problem or not.

---

### Post by vasa1 on 2012-06-29
> **rattata said:**
> ...
Through some searching, I haven't found any mention of the problem I'm having. Maybe I'm not looking hard enough, I don't know. I have no idea if this is a common problem or not.

Have you considered asking at the Mint forum?

---

### Post by rattata on 2012-06-29
> **vasa1 said:**
> Have you considered asking at the Mint forum?

I was thinking of posting this there as well, but I wasn't sure if it made sense as I'm using Ubuntu. For all I know, it could be the fact that I'm using Cinnamon on Ubuntu 12.04. Although, I think it's more likely a problem with my computer, as it also has issues with Elementary and possibly Fedora. :s

---

### Post by praveenthivari on 2012-06-30
This link could be of help to you. I did have similar problems:

[http://askubuntu.com/questions/143838/restart-cinnamon-from-tty](http://askubuntu.com/questions/143838/restart-cinnamon-from-tty)


Basically you have to run to commands from tty1:
(To go to tty use ctrl+Alt+F1)
```
killall -9 cinnamon
```

and then, restart cinnamon using:
```
export DISPLAY=:0.0; cinnamon
```

---

### Post by wheeze on 2012-06-30
> **rattata said:**
> ...I'm using Cinnamon on Ubuntu 12.04.

Cinnamon + Ubuntu 12.04 = Mint 13. Should work fine.

There are lots of 12.04 lockup/slowdown threads. Seems to be a problematic release in this regard.

---

### Post by vasa1 on 2012-06-30
> **wheeze said:**
> Cinnamon + Ubuntu 12.04 = Mint 13. Should work fine.

There are lots of 12.04 lockup/slowdown threads. Seems to be a problematic release in this regard.

I happen to think that the Ubuntu + Cinnamon combination hasn't been tested enough whereas the Cinnamon + Mint combination obviously may have had more testing.

I don't find 12.04 to be a "problematic release" at all when using Unity 2D or Unity 3D or Xfce 4.10.

---

### Post by wheeze on 2012-06-30
> **vasa1 said:**
> I happen to think that the Ubuntu + Cinnamon  combination hasn't been tested enough whereas the Cinnamon + Mint  combination obviously may have had more testing.

I'm running a Cinnamon/12.04 setup here, installed from Ubuntu mini.iso. Working just fine.

> **vasa1 said:**
> I don't find 12.04 to be a "problematic release" at all when using Unity 2D or Unity 3D or Xfce 4.10.

The number of "frozen system" postings tends to indicate otherwise. Seems to be a split personality release. It either works fine for you (and me) but is a bugger for others.

---

### Post by rattata on 2012-06-30
> **praveenthivari said:**
> This link could be of help to you. I did have similar problems:

[http://askubuntu.com/questions/143838/restart-cinnamon-from-tty](http://askubuntu.com/questions/143838/restart-cinnamon-from-tty)


Basically you have to run to commands from tty1:
(To go to tty use ctrl+Alt+F1)
```
killall -9 cinnamon
```and then, restart cinnamon using:
```
export DISPLAY=:0.0; cinnamon
```

Thanks, I'll try this next time it happens and update this thread. =)

---

### Post by DMGrier on 2012-06-30
I used cinnamon and it seemed to work good for me but from what I watched on the Linux action show they said the amount of maintenance in it is going to be  a lot of work. Don't know it this is true cause I am not a programmer but I am fine with the Unity.

---

