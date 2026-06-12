---
title: "Flat Panel and Docking Station"
date: 2007-07-26
forum: Dell  Ubuntu Support
---

### Post by rshol on 2007-07-26
Running a Dell Latitude D820 with an nVidia graphics card and a standard install of ubuntu feisty.  I want to use the laptop with a Dell docking station which is attached to a Dell flatpanel monitor.  I get no video from the flat panel monitor when the laptop is attached to the docking station.  

I have been looking for a solution to this problem for a long time and surely there must be an answer.   I have tried every recommended xorg.conf setting I can find that is even remotely applicable, and have installed various versions of linux (Mepis, Linux Mint, SuSE) with the same results.

The display works fine without the nVidia driver, but I want open gl support and hardware acceleration.

Now that Dell is shipping with Ubuntu installed I thought someone might know of a fix.

---

### Post by kansei on 2007-08-05
Have you run nvidia-settings ? I'm on a D620 hooked up to a dock with a DVI flat panel right now ..  I can get video on the second display, but it isn't functional (I can't put windows over there, but I can see the mouse pointer there. I'm using Gutsy Gibbon though so my issue may be related to some pre-release software.

---

### Post by GrammatonCleric on 2007-08-15
I've got my D820 running with both an Apple Cinema Display and the native LCD on the laptop.   

1.) The Key is installing the NVidia drivers, I was lazy and used [**Envy**]("http://albertomilone.com/nvidia_scripts1.html") to do this.  

2.) Once the NVidia drivers are installed reboot and leave your external LCD diconnected from the laptop or dock.

3.) Log back into your laptop.  

4.) Plug in your external LCD. 

5.) Now, open a terminal.

6.) In the terminal type:

```


sudo /usr/bin/nvidia-settings


```This will bring up the nvidia x server settings gui.  The reason for doing this with the "sudo" is once you 
have the settings the way you want you can actually save them to the xorg.conf.

7.) In the nvidia x server settings gui select "X Server Display Configuration."

8.)  You should see your external LCD but it should be disabled.  Select the "disabled" monitor and click on the configure  button.

9.) Now you can selected either Twinview or Separate X Screen.

From this point you should be able to tweak things to your liking.  

Be sure that when you save your changes do not "merge" them into your current xorg.conf but rather overwrite the current.  By default  a backup copy should be created each time you do this.

-GC

---

### Post by kansei on 2007-08-15
oh wow I think this whole time I might not have been running it with sudo *doh*

i'm pretty sure I just hit alt+f2 and ran nvidia-settings.. I was wondering why none of my settings were persisting.

THANKS nvidia for not giving any error messages when saving my xorg.conf you bastids

---

