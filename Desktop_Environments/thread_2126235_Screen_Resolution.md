---
title: "Screen Resolution"
date: 2013-03-16
forum: Desktop Environments
---

### Post by oakridge on 2013-03-16
With the discovery of Fotoxx I can now do everything on Ubuntu that I have done with Windows in the past, so the time has come to swap the two machines.  The Windows 7 has a wide screen monitor at 1920*1080 which is better for me because I do not see very well.  The resolution is not listed on the Ubuntu settings which is a bit of a problem so is there any way around this please?

Malcolm

---

### Post by sudodus on 2013-03-16
Please describe your system, or at least the graphics card/chip and the graphics driver (built-in or proprietary)

And it would help start a dialogue, if you post the output of
```
xrandr
```

---

### Post by oakridge on 2013-03-16
xrandr:

oakridge@oakridge:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1280
DFP1 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 340mm x 270mm
   1280x1024      60.0*+   75.0  
   1280x800       60.0 +   75.0  
   1280x720       60.0 +
   1280x960       75.0     60.0  
   1152x864       75.0     60.0  
   1280x768       74.9     59.9  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     70.0     60.3  
   720x480        60.0  
   640x480        75.0     72.8     60.0  

This is using an HP L1710 monitor, but it read the same on the widescreen.

The drivers are as they come with Ubuntu version 12..04 LTS.

The graphics driver is ATI/AMD proprietary FGLRX.

I hope this helps.

Malcolm

---

### Post by sudodus on 2013-03-16
> **oakridge said:**
> xrandr:

oakridge@oakridge:~$ xrandr
...
   1280x1024      60.0*+   75.0  
   ...
   1280x720       60.0 +
   ...
This is using an HP L1710 monitor, but it read the same on the widescreen.
The drivers are as they come with Ubuntu version 12.04 LTS.
The graphics driver is ATI/AMD proprietary FGLRX.
I hope this helps.
Malcolm

I guess the current resolution 1280x1024 is the same as the native resolution for the  HP L1710 monitor, so it is OK. But the wide screen is not recognized. I see that there is one 16x9 resolution listed, 1280x720, but that may not make you very happy. The cooperation between linux and ATI/AMD is not perfect, but I know people manage to get it fairly good after some tweaking. [COLOR=#808080]I have nvidia and intel graphics, so I don't know much about your kind of chips and drivers.[/COLOR]

Maybe you can run ```
jockey-gtk
``` to revert back to the open-source driver, and see if that will see the native resolution of your wide-screen monitor.

Otherwise there are tutorials on the internet and threads at the Ubuntu Forums, how to use xrandr and some help programs to create custom resolutions, that might work, even if they were not found or created automatically by the system. (This means that xrandr would see a 1920x1080 mode, and you would be able to select it.)

---

### Post by sudodus on 2013-03-16
See this thread

[[COLOR=#ff0000]http://ubuntuforums.org/showthread.php?t=2121613[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2121613")

---

### Post by oakridge on 2013-03-16
Thank you for your reply.

This is going to take me a while to work through, so I will come back to it in due course.

Malcolm

---

### Post by grahammechanical on 2013-03-16
I am not clear about what you are trying to do. Do you have two machines? One with Windows 7 and a monitor running at 1920*1080? and another running Ubuntu? Have you tried connecting the 1920*1080 resolution monitor to the Ubuntu machine?

When Ubuntu loads the display driver gets the monitor settings from the monitor (Extended Display Identification Data) and the video driver then runs the monitor at the optimum settings chosen by the manufacturer. This is why we do not need to select monitor resolution settings or choose a monitor at the time of installing Ubuntu.

[http://en.wikipedia.org/wiki/Extended_display_identification_data](http://en.wikipedia.org/wiki/Extended_display_identification_data)

This is why the Ubuntu Displays utility or the proprietary video driver settings utility will not offer a screen resolution greater than the optimum recorded in the monitor's EDID.

Regards.

---

### Post by sudodus on 2013-03-16
Inspired by  				 					 						 							 						 					 				 				 					 						 	grahammechanical, I'm asking:

Did you switch the monitors while the computer was powered off? If not, please do, and give Ubuntu a chance to boot with the widescreen monitor connected!

---

### Post by oakridge on 2013-03-17
Thank you sudodus and grahammechanical for your replies.

Yes there are two machines; one Windows 7 with a 23" 1920*1080 monitor and the Ubunto currently on the standard HP monitor.  Now that I can do pretty well everything I need to do as well, and in some cases better, with the Ubuntu I want to swap monitors.  As I have said my eyesight is very poor and the large monitor is easier to see and it is on an arm so I can get within the 4" of my nose which I require.  It does have the disadvantage that the mouse pointer can take a bit of finding on occasions.  
The Acer running Windows is not in the first flush of youth, 1997 I think.

Because the large monitor is fixed and the machines are on different desks there was no question of keeping the machines powered up during change over, but I probably did not turn the monitors off.

When I turned the Ubuntu on after switch-over it did not take account of the new monitor.

I hoipe that has cleared the fog a bit.

Malcolm

---

### Post by sudodus on 2013-03-17
Yes, I see. Ubuntu 'should have' found the proper resolution of the wide screen monitor, but did not.

1. I think you can ***try along the path of that link I supplied*** to another thread in the Ubuntu Forums. It might work for you too.

2. You can also ***try Ubuntu*** from the Ubuntu install CD/USB drive while the computer is connected to the wide-screen monitor. Do not install at once, only run a live session to try Ubuntu! Then it is not pre-set to anything else, but starts from the beginning, and let us hope, finds the monitor and configures itself to it. If this is the case, you should consider reinstalling Ubuntu, it might be easier than to find the problems and repair the present installed Ubuntu system. But first backup all your personal data!

---

### Post by oakridge on 2013-03-17
Thank you sudodus.

I will follow your first suggestion and the first part of the second and strongly hope that it does not come to a re-installation.  Three of us in household work from home and the Ubuntu acts as an excellent file server.  It was bad enough changing from the failing Mandriva to Ubuntu in late 2011, to make me put off a such drastic action as long as possible.

Malcolm

---

### Post by sudodus on 2013-03-17
Good luck :-)

---

### Post by oakridge on 2013-03-17
This message seems to have got itself repeated....

Thank you sudodus and grahammechanical for your replies.

Yes there are two machines; one Windows 7 with a 23" 1920*1080 monitor and the Ubunto currently on the standard HP monitor.  Now that I can do pretty well everything I need to do as well, and in some cases better, with the Ubuntu I want to swap monitors.  As I have said my eyesight is very poor and the large monitor is easier to see and it is on an arm so I can get within the 4" of my nose which I require.  It does have the disadvantage that the mouse pointer can take a bit of finding on occasions.  
The Acer running Windows is not in the first flush of youth, 1997 I think.

Because the large monitor is fixed and the machines are on different desks there was no question of keeping the machines powered up during change over, but I probably did not turn the monitors off.

When I turned the Ubuntu on after switch-over it did not take account of the new monitor.

I hoipe that has cleared the fog a bit.

Malcolm

---

### Post by oakridge on 2013-03-18
I have chickened out, as they say, in the short term.

The solution outlined in the link was more than a little beyond my skill level so I must do some further reading.  If anyone can push me in the right direction I would be most grateful.  In the meantime I have pressed the 'aspect' button on the remote so the display is now better proportioned albeit not using the whole screen.

Thank you for all your help, er, so far.

Malcolm

---

### Post by sudodus on 2013-03-18
Did you try this: boot from the Ubuntu install CD/USB  drive ?

You can also ***try Ubuntu*** from the Ubuntu install CD/USB  drive while the computer is connected to the wide-screen monitor. Do not  install at once, only run a live session to try Ubuntu! Then it is not  pre-set to anything else, but starts from the beginning, and let us  hope, finds the monitor and configures itself to it.

---

### Post by oakridge on 2013-03-19
I have run 'try Unbuntu' from the CD, but it sticks to 4:3 aspect ration.  I have evern tried the Microsoft Method; turn absolutely everything off and restart.

I can live with the situation as is for a while and it is much better quality than the HP monitor.  

There is another small problem which I think I will move onto for a while.

I am extremely grateful for all your help with this problem.

Malcolm

---

### Post by sudodus on 2013-03-19
If Ubuntu cannot cooperate with the hardware, feel free to try another linux distro. ***Knoppix*** is known to detect and cooperate with a lot of hardware, also aging hardware, so I suggest that you download and make a boot CD/DVD or USB drive with Knoppix and try if it will give you the full screen resolution with your wide screen monitor.

See [[COLOR=#ff0000]http://www.knoppix.org/[/COLOR]]("http://www.knoppix.org/")

---

### Post by oakridge on 2013-03-19
Yes, thank you for that, it looks very interesting.  I will try it.

Malcolm

---

### Post by oakridge on 2013-04-01
Sorry for the long delay.  I have experimented with Knoppix and I am now getting just a small margin at each side of the screen with no distortion, so this is quite satsifactory for me.

Thank you.

Malcolm

---

### Post by sudodus on 2013-04-01
Congratulations :KS

---

