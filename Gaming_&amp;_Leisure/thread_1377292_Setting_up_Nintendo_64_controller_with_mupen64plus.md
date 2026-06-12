---
title: "Setting up Nintendo 64 controller with mupen64plus"
date: 2010-01-10
forum: Gaming &amp; Leisure
---

### Post by putamaster on 2010-01-10
I'm currently have a bit of trouble getting my old nintendo 64 controller to work with mupen64plus 1.99.1 on mythbuntu 9.04. Reading around forms and the like I feel like I'm missing something with my mupen64plus install. As far as I can tell I've only got a CLI version which opens a window with no menus. It kinda sounds like there should be a GUI version or something, is this correct?

Other wise so far I can happily play roms using the keyboard. Using jstest I can see that input is being picked up from the controller on /dev/input/js0. I'm just not sure how to go about telling mupen64plus to use the controller and/or map the keys.

Any help would be much appreciated.

---

### Post by mister_playboy on 2010-01-10
Mupen64 definately has a GUI... it's hard to say what you have installed.

Here's the project page:

[http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/)

Start by getting the latest version and go from there.

How are you hooking up the N64 controller?  Do you have a USB adaptoid?  Those are pretty rare... I'm jealous, since I've never found a good way to map the N64 keys to the PS2 controller I use for emus. :)

---

### Post by adeypoop on 2010-01-10
As I understand it, previous versions of mupenplus **did** have a GUI whereas the latest version does not. Apparently some major changes have been made to make mupenplus be more modular or something, presumably to make it better. In order to run a ROM  you currently use the terminal. The controller is supposed to be automatically detected and configured.

This would be fine except I cannot get my Saitek controller working in the new version, therefore I have to continue using an older version.

I am interested if anyone knows a way to configure controllers in the latest version ..

---

### Post by putamaster on 2010-01-11
Thanks for the replies. I did get the latest version from the [http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/) site, but by the sounds of it I may need to try an earlier version (will look into this tomorrow).

As for the setup, yes I am using an original N64 controller with a USB adapter. Went to relive some old games a while ago and found the N64 wasn't working. Was checking on ebay to see how much a replacement would cost when I found the USB to controller devices.

---

### Post by putamaster on 2010-01-12
I got my controller setup and running using mupen64plus version 1.5. Still got the option to launch roms from the CLI with no GUI which works well once you've setup your preferences. Will see what happens, mite try and get the new version up and running latter down the track when I have more time.

---

