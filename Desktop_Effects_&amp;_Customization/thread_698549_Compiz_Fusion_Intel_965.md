---
title: "Compiz Fusion Intel 965"
date: 2008-02-16
forum: Desktop Effects &amp; Customization
---

### Post by thecorleonefamily on 2008-02-16
I have an Intel 965 motherboard and unfortunately the onboard graphics thing has been blacklisted by Compiz Fusion.

I did get it working by editing the /usr/bin/compiz thing but I have a few questions.

1. Since video was not working, I choose X11 Video Output instead of the default in VLC (which I guess is xv). What is the difference?

2. Ring Switcher doesn't work. Is this expected?

3. In a post on this forum, someone had posted and I quote:

" 

Quote:
sudo gedit /etc/X11/xorg.conf
Paste the following into the bottom of the xorg.conf file, save and reboot.


Quote:
Section "Extensions"
Option "Composite" "enable"
EndSection

", 

The user claims that he got video working. Should I try this? I am afraid to do it since I have a stable system and I don't want to mess this up.

Any help will be appreciated. Thanks!

---

### Post by reacocard on 2008-02-16
> **thecorleonefamily said:**
> I have an Intel 965 motherboard and unfortunately the onboard graphics thing has been blacklisted by Compiz Fusion.

I did get it working by editing the /usr/bin/compiz thing but I have a few questions.

1. Since video was not working, I choose X11 Video Output instead of the default in VLC (which I guess is xv). What is the difference?

2. Ring Switcher doesn't work. Is this expected?

3. In a post on this forum, someone had posted and I quote:

" 

Quote:
sudo gedit /etc/X11/xorg.conf
Paste the following into the bottom of the xorg.conf file, save and reboot.


Quote:
Section "Extensions"
Option "Composite" "enable"
EndSection

", 

The user claims that he got video working. Should I try this? I am afraid to do it since I have a stable system and I don't want to mess this up.

Any help will be appreciated. Thanks!

1) X11 lacks any hardware acceleration of video, and typically scales videos less well. If you can, get mplayer with the compiz video patch, which at least allows hardware-accelerated scaling. 

2) It works fine for me on the same card, so it must just be something in your setup.

3) It shouldn't hurt anything, but in theory that tweak is applied by default in the current Ubuntu xorg even if that section is not present so I wouldn't expect it to make a difference. Try it and let us know if it does.

---

### Post by thecorleonefamily on 2008-02-16
So that means if I use mplayer with the patch, I can playback video (fullscreen) ?

---

### Post by reacocard on 2008-02-16
> **thecorleonefamily said:**
> So that means if I use mplayer with the patch, I can playback video (fullscreen) ?

correct. I use it myself all the time, it works perfectly.

---

### Post by mliang2 on 2008-02-24
My dell vostro had the same problem.   I upgraded to hardy alpha for the newer xorg intel driver, it's not completely fixed.  Compiz runs, but it uses alot of cpu/load.  

Workaround: uninstall compiz and use beryl from feisty.   Add the feisty universe repository and aptitude install beryl.   Run the beryl manager and you'll get the gem icon on the system tray.  When you want to play video, right click the beryl manager and switch back to the old window manager.   When you're  done, reactivate beryl.  

Beryl doesn't have the severe cpu load I get when running compiz.

---

### Post by Amaranth on 2008-02-24
And have absolutely no support and many many bugs. Awesome solution.

---

### Post by magnat2 on 2008-02-25
> **reacocard said:**
> 1) X11 lacks any hardware acceleration of video, and typically scales videos less well. If you can, get mplayer with the compiz video patch, which at least allows hardware-accelerated scaling. 

2) It works fine for me on the same card, so it must just be something in your setup.

3) It shouldn't hurt anything, but in theory that tweak is applied by default in the current Ubuntu xorg even if that section is not present so I wouldn't expect it to make a difference. Try it and let us know if it does.
Theres a way to watch videos with compiz desktop effects on, in gconf editor go to multimedia system selector and in the video area put "window system ( no xv) in options and you have videos without having to turn desktop effects off, i have an acer aspire 5720 with that graphics card, any doubts go-to: [http://acer5720linuxubuntu.blogspot.com/](http://acer5720linuxubuntu.blogspot.com/)
Good luck!

---

