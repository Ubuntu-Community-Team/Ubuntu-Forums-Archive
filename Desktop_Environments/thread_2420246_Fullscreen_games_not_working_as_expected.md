---
title: "Fullscreen games not working as expected"
date: 2019-06-01
forum: Desktop Environments
---

### Post by h-corbin on 2019-06-01
I am having an issue with fullscreen games.   
This is happening with all fullscreen games, but I'll use Dosbox as an example.
If I have a game open running at 640x480, and set it to fullscreen, I will get a 640x480 dosbox surrounded by black bars on all 4 sides.  
I expect it to resize my screen to 640x480 (stretching the aspect ratio), or at least resize so that the game is full height and I get black bars left and right to maintain the aspect ratio.

I have tried googling, but cannot seem to find the right keywords for this issue.
I have tried searching ubuntu forums, and have the same problem.

I am running:
Lubuntu 18.04
nvidia proprietary drivers (I see the same result with open drivers).
native screen 1920X1080

HP Omen laptop 
nvidia geforce gtx 1050

---

### Post by Dennis N on 2019-06-01
As far as DosBox is concerned, you enable full screen for the game window in the **~/.dosbox/dosbox-0.74.conf** file. Try setting **fullscreen=true**. 
```
# This is the configurationfile for DOSBox 0.74. (Please use the latest version of DOSBox)
# Lines starting with a # are commentlines and are ignored by DOSBox.
# They are used to (briefly) document the effect of each option.

[sdl]
#       fullscreen: Start dosbox directly in fullscreen. (Press ALT-Enter to go back)
#       fulldouble: Use double buffering in fullscreen. It can reduce screen flickering, but it can also result in a slow DOSBox.
#   fullresolution: What resolution to use for fullscreen: original or fixed size (e.g. 1024x768).
#                     Using your monitor's native resolution with aspect=true might give the best results.
#                     If you end up with small window on a large screen, try an output different from surface.
# windowresolution: Scale the window to this size IF the output device supports hardware scaling.
#                     (output=surface does not!)
#           output: What video system to use for output.
#                   Possible values: surface, overlay, opengl, openglnb.
#         autolock: Mouse will automatically lock, if you click on the screen. (Press CTRL-F10 to unlock)
#      sensitivity: Mouse sensitivity.
#      waitonerror: Wait before closing the console if dosbox has an error.
#         priority: Priority levels for dosbox. Second entry behind the comma is for when dosbox is not focused/minimized.
#                     pause is only valid for the second entry.
#                   Possible values: lowest, lower, normal, higher, highest, pause.
#       mapperfile: File used to load/save the key/event mappings from. Resetmapper only works with the defaul value.
#     usescancodes: Avoid usage of symkeys, might not work on all operating systems.

[COLOR="#FF0000"]fullscreen=false[/COLOR]
fulldouble=false
fullresolution=original
windowresolution=1000x750
# original > 800x600
output=overlay
[trimmed here]
```

---

### Post by h-corbin on 2019-06-01
Thanks for the information, but my issue is not with making dosbox fullscreen.  I am able to make dosbox fullscreen, but when it is fullscreen my screen resolution does not change, meaning that the dosbox content is centered with black bars all around it.  This is not only happening with dosbox, I only used dosbox as an example.

BTW, I tend to start dosbox windowed and fullscreen it by hitting alt-enter.
I get the same result whether I edit the conf file and set it to fullscreen, or I start it windowed and hit alt-enter.

---

### Post by Dennis N on 2019-06-02
Notice that there is also a setting for **windowresolution=** if you want the DosBox window larger. I keep the ratio at 4:3 as the original games usually were back in the 90s. In the display in post #2, 1000x750 is still 4:3.

---

### Post by h-corbin on 2019-06-04
I guess using DosBox as an example was a bad choice.  I am not looking for assistance with DosBox.

I am not having an issue with dosbox specifically, but with fullscreen apps not resizing the desktop when they are fullscreened.
Another example is the puzzle game Einstein.  There are no resolution settings for this app that I can find.  The only options are windowed and fullscreen.
In previous versions of Ubuntu, fullscreen for this app would stretch to fill the screen, changing the screen resolution in the process.
In Ubuntu 18.04 on my old laptop, it would stretch to fill the screen, but preserve the app's aspect ratio by placing black bars to the left and right.  The screen resolution would get changed.
In Ubuntu 18.04 on my new laptop, it does not change the screen resolution.  Instead, the game window gets centered and black bars fill the remaining space on top, bottom, left, and right.
I want the previous behavior where the screen resolution gets changed when the game is in fullscreen mode.

Again, I am not looking for assistance with DosBox, I am looking for assistance with my X server.

---

### Post by CatKiller on 2019-06-04
LCDs and LEDs are a fixed array of pixels. They *only* have one resolution, unlike CRTs.

When using a lower resolution than the native one the signal is only sending information about *some* of those pixels, so information about all the *other* pixels has to come from somewhere else - a scaler.

Applications like DOSBox, or MAME, or ScummVM, expect their sources to have much fewer pixels than the display, and so include a variety of configurable scalers for turning a small number of pixels into a larger number of pixels. Drivers, which take the pixels from an application and send them to a display, can also introduce a scaler. Displays themselves can also include a hardware scaler to turn the small number of pixels from the signal into a larger number of pixels to go on the screen, although the very earliest didn't. The quality of each of these implementations can vary, which is why all of them exist. The X Server does not have a scaler of its own.

In your case, the difference in behaviour is likely because your display is configured differently. Most displays have the option for whether to make up some extra pixels, or just leave them black, or some combination of the two. For monitors, this setting will be exposed through the menu. For laptops, this setting will be exposed through the BIOS.

---

### Post by h-corbin on 2019-06-06
Thanks for the reply.  I pulled the drive from my old laptop and booted the new laptop from it and it was doing the same thing with fullscreen apps having black bars all around.  Since ms windows on the same laptop is able to scale fullscreen apps, I suspect that there must be something in the nvidia driver to allow the scaling.  Might be a hidden option, will likely require more digging to find.

---

