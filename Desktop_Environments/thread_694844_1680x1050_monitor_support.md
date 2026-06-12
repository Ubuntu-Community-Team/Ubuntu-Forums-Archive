---
title: "1680x1050 monitor support?"
date: 2008-02-12
forum: Desktop Environments
---

### Post by Venor on 2008-02-12
I was able to install Ubuntu on a family members older dell yesterday no problem.
Today I am trying on my own computer. When I boot from the CD I can see the boot screen no problem. The install disk doesn't have an option for my monitor size nor does any of the options available support my monitor 1680x1050. When I proceed with the install I just get a black screen. Does anyone have an idea of how to get around this?

---

### Post by taurus on 2008-02-12
What is the spec of your machine?  You can either use the safe mode from the menu when you first boot the CD or you can always use the alternate CD to install Ubuntu on your machine.

---

### Post by Venor on 2008-02-12
e6800 2gb ram 8800 gtx asus p5w dh deluxe.

I will try those alternate ways again.

---

### Post by Venor on 2008-02-12
Still no luck.

---

### Post by pbcartwright on 2008-02-12
you didn't say how far you get in the install. I have an older Dell with an NVIDIA card, and I install ubuntu/SUSE/whatever linux on it all the time. what boot options do you have?? I remember problems, I had to use the noapic install I think...

---

### Post by noremac on 2008-02-12
I had a similar problem when I installed Ubuntu(also, with a 1680x1050 screen). I just had to select the "safe graphics mode" at the initial boot up screen and I had no issue after that. 

-Cameron

---

### Post by Venor on 2008-02-12
I can't get past the first part of the install screen. The install does proceed but I can't see anything.

---

### Post by taurus on 2008-02-12
Even with the alternate CD?

---

### Post by Venor on 2008-02-13
Ok I pretty pissed atm. I use the alternate CD nuked a partition I didn't want to nuke and on top of that when the install completes, restarts and starts up I get a black screen. Nothing.
I piss around with this for an hour using both install cd's trying to get in by safe mode. Finally I get in by using the esc to grub option and then magically I am in ubuntu I think in safe mode. Now what? If I save my settings in safe mode can this work or can I get some tips here to make sure that nothing else goes wrong?

---

### Post by Venor on 2008-02-13
So it would have been handy if someone in the community or staff had told me that the 8800 isn't supported? According to the message within recovery mode there is a driver but not supported. 

Yes I keep getting a black screen on start up. The only way to get in is recovery mode then terminate the shell it goes in to. So what the heck am I doing wrong?

I am using and e6800, p5w dh asus, 2gb ram, 360gb hard, 8800 gtx and a Samsung 225 bw if that makes any difference.

---

### Post by hardyn on 2008-02-13
1) check the driver release details, if you board is not supported, its not supported.

I am running that res, with pretty much no trouble... however, ubuntu was really keen on performing that resoultion with 75hz refresh, which would overscan most LCD displays, you may have to edit the xorg.conf file to force the refresh to 60hz.

---

### Post by Venor on 2008-02-13
NVIDIA accelerated graphics driver (lastest cards)    is the warning I have under restricted devices.
When I look further in to screens and graphics in the system/admin pull down I have set up the correct devices there. It cannot auto detect these devices.
When I look under preferences/device manager I can find G80 [Geforce 8800 GTX]


I installed the 64 bit version of Ubuntu. Would the 32 bit make any difference?

---

### Post by Venor on 2008-02-13
so it looks like people are gonna stay away from this one...

---

### Post by KIeranG on 2008-02-13
I had this issue today too

1.) Make sure it's the latest version of Ubuntu, 7.10...

2.) Try this in terminal:

sudo dpkg-reconfigure xserver-xorg

Select 'nv' or 'nvidia' and go through the set up, their is a stage where you can pick a resolution (1680x1050 is there.)

Good luck...

---

### Post by Venor on 2008-02-13
Thank you for the help. Still doesn't work. I have a feeling it is not getting to the start up screen. A stall or crash maybe.

---

### Post by KIeranG on 2008-02-13
If you have a GUI click on system, then administration, and then "screens and graphics"... I found a way to get my resolution on that screen... make sure "widescreen is ticked" and under generic, just look for your resolution... or look for your actual monitor on the list...

gl,
Kieran

---

### Post by Gambini on 2008-02-13
I had the same problem, but I used Envy for the driver. I can't remember what I did, but somehow it worked after I installed the driver. Envy can be found here: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html). (except I'm using an 8800GT rather than GTX, but I can't imagine it would make much of a difference.)

---

### Post by Venor on 2008-02-13
Envy didn't solve anything. But thanks for the suggestion. It does load the proper drivers. But still I have black screen after grub loads.

---

### Post by Venor on 2008-02-13
Looks like I'm going back to winblows

---

### Post by Gambini on 2008-02-14
Did you delete the old driver before installing the new one? I've read at some places (don't remember where) that there are errors if you don't uninstall the old driver before installing the new one. That might fix the black screen, and it wouldn't try to hurt.

---

### Post by angryfirelord on 2008-02-14
Here's what I have to offer:

First, get into safe mode. If you can't load X, then try logging in at terminal (you may need to press Ctrl+Alt+F1). If you have Gnome loaded, then open up gnome-terminal.

Remove the nvidia drivers:
```
sudo apt-get remove nvidia-glx nvidia-glx-new
```
Re-install the new nvidia driver:
```
sudo apt-get install nvidia-glx-new
```
Now, run this command:
```
sudo dpkg-reconfigure xserver-xorg
```
Select nvidia as your driver. Accept defaults (unless you know what they mean) until you hit the resolutions at the end. Select "1680x1050" "1024x768" "800x600" & "640x480" (and any other resolutions you think your monitor supports. Then, at the next slide, select Medium. Finally, select "1680x150" @ 75 Hz and 24-bit color (make sure you say yes to save configuration when it asks you). Reboot and you should have your widescreen resolution.

Tutorial for dpkg-reconfigure xserver-xorg: [http://www.youtube.com/watch?v=2QsP8GDTpno]("http://www.youtube.com/watch?v=2QsP8GDTpno")

---

