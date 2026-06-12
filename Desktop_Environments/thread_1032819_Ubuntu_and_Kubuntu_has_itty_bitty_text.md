---
title: "Ubuntu and Kubuntu has itty bitty text"
date: 2009-01-06
forum: Desktop Environments
---

### Post by hougSTAR on 2009-01-06
Yo.

So, Ubuntu was working fine and dandy one day.  Until one day I turned it on and had itty bitty text on the login screen when I typed in my info.  It is like that on all the menus, but it is fine when I look at websites.  It also does this to Kubuntu (just installed it too).

I can barley make out, if at all, what the text is on the menu screens.  Is there something I can do to make the font size larger (aka normal like it used to be)?

---

### Post by skern03 on 2009-01-06
> **hougSTAR said:**
> Yo.

So, Ubuntu was working fine and dandy one day.  Until one day I turned it on and had itty bitty text on the login screen when I typed in my info.  It is like that on all the menus, but it is fine when I look at websites.  It also does this to Kubuntu (just installed it too).

I can barley make out, if at all, what the text is on the menu screens.  Is there something I can do to make the font size larger (aka normal like it used to be)?

Right-click on the desktop and choose Change Desktop Background. Click the Appearances tab, and see what the font sizes are there. That may solve it for you. I've attached an image.

---

### Post by jclose on 2009-01-08
I am having a similar problem, but mine started from the moment I installed the system.  I installed Kubuntu 8.10 from scratch and was greeted with tiny fonts in all the windows and text.

I was able to find the appearance -> Fonts section and change the size from about a 9 pt size to 17 pt or so (using the "Change all Fonts" method), and that helped significantly for most applications.  But there are still areas that have the tiny fonts:  the login screen and the package manager (sorry, forgetting the name at the moment) screen are the two that stand out the most.  I can get by the login screen without much difficulty, but the package manager screen makes it impossible to read anything and I can't update stuff!  

My video driver had defaulted to Vesa on the install, and I finally managed to get an Nvidia driver installed I think.  But that doesn't seem to have changed anything with the login screen and the package manager, except the font size in the Hardware Device Settings screen is now large enough to read (it was also very small before).

Oh, it is an Nvidia 6200LE video card (AGP), and it is connected to my plasma TV in the front room, 1024x768 native res (HP PL4260).


Any suggestions?  

Thanks,
Justin

---

### Post by skern03 on 2009-01-08
> **jclose said:**
> I am having a similar problem, but mine started from the moment I installed the system.  I installed Kubuntu 8.10 from scratch and was greeted with tiny fonts in all the windows and text.

I was able to find the appearance -> Fonts section and change the size from about a 9 pt size to 17 pt or so (using the "Change all Fonts" method), and that helped significantly for most applications.  But there are still areas that have the tiny fonts:  the login screen and the package manager (sorry, forgetting the name at the moment) screen are the two that stand out the most.  I can get by the login screen without much difficulty, but the package manager screen makes it impossible to read anything and I can't update stuff!  

My video driver had defaulted to Vesa on the install, and I finally managed to get an Nvidia driver installed I think.  But that doesn't seem to have changed anything with the login screen and the package manager, except the font size in the Hardware Device Settings screen is now large enough to read (it was also very small before).

Oh, it is an Nvidia 6200LE video card (AGP), and it is connected to my plasma TV in the front room, 1024x768 native res (HP PL4260).


Any suggestions?  

Thanks,
Justin

9 pt fonts should be fine. What's your resolution? I'm wondering if that's your problem. Not sure if this works in Kubuntu... I threw that out after the browbeatings and lack of support on the k-forum. Open a terminal and enter this command:
> sudo xrandr -q
That should produce a list of supported resolutions, including the current resolution. The first line of output for me is:
> Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1680 x 1200
If you want to set the resolution "by hand" you can enter:
> sudo xrandr -s 1024x768

As for the boot screen, you can set the resolution for the boot loader. In Ubuntu, you can load a boot manager like so (bypassing the problem you have with the package manager):
> sudo apt-get install startupmanager
In Kubuntu, I *think* there's a boot manager already loaded. The boot manager will let you set the screen resolution (but not the fonts) in the startup screen.

HTH...

---

### Post by JRAltd on 2009-11-02
What is the boot manager for Kubuntu and how do you access it so I can make the needed changes to fix this problem.
Thank you, :)

---

### Post by skern03 on 2009-11-02
> **JRAltd said:**
> What is the boot manager for Kubuntu and how do you access it so I can make the needed changes to fix this problem.
Thank you, :)

Wish I could help, but I gave up on Kubuntu more than a year ago. You can try their forums, but frankly, the Kubuntu forums are the reason I gave up on Kubuntu and now only use Ubuntu. Folks here are polite and always helpful!

---

