---
title: "How to select or delete options in xserver-xorg?"
date: 2009-09-14
forum: Desktop Environments
---

### Post by A Traveller on 2009-09-14
Hi All.

I installed my Linux hard drive yesterday (Ubuntu 6.06) and initially, the Linux window was too small on my big monitor. I tried changing the resolution via Preferences, but it only had one option (640 x 480) so I did a search on the net and learnt that entering 'sudo dpkg-reconfigure xserver-xorg' would allow the screen resolution to be changed.

I carried out the above instructions and got to the point where I get the following info (not before I had to research the Internet for info on why my password didn't seem to be typing!):

Configuring xserver-xorg
If there are some resolutions you would not like the X server to use‚ even if your hardware is capable of them, remove them from the list below. Removing all of them is effectively the same as removing none‚ since in both cases the X server will attempt to use the highest‚ possible resolution. Select the video modes you would like the X server to use.

[ ] 1920x1440
[ ] 1920x1200
[ ] 1856x1392
[ ] 1792x1344
[ ] 1680x1050
[ ] 1600x1200

<Ok>

(The list goes all the way down to 640 x 480. Up to 1024 x 768 have an asterisk in the closed brackets in front of them. I'm guessing that this means that they are selected. The rest of them are blank.)

I have tried searching the Help files, the Internet and pressing nearly every key on the keyboard but can't seem to figure out how to 'select' any of the resolutions or 'delete' any of them.

How is this done?

(I restarted in the end and the window is now bigger and the options in Preferences now include up to 1024 x 768, but how do I SELECT 1920 x 1200? What keyboard keys are used for selecting.)

I knew Linux was a huge learning curve, but I never thought you had to go through ten million pages of irrelevant questions in order to change the screen resolution!

Any help will be appreciated. Thanks.

---

### Post by 3rdalbum on 2009-09-14
Stop what you're doing right away, and download Ubuntu 9.04.

Ubuntu 6.06 is much too old to work on your hardware. 6.06 is end-of-life on desktops and it's so old that we probably don't remember much about its foibles and the way you did things in Ubuntu back in 2006.

To answer your question, you select items in the menu by pressing the space bar, but this whole procedure you're going through is not necessary these days with Ubuntu 9.04.

---

### Post by A Traveller on 2009-09-14
Hi 3rdalbum. Thanks for your reply.

The reason I haven't yet got the latest version of Ubunutu is because my computer is about ten years old! I am in the process of getting new equipment, which I am FINALLY getting around to now, after having intended to do so a LONG time ago!

Thanks for the space bar info. I don't believe it. I must have tried every other key on the keyboard except the space bar! I'm slightly puzzled though about why I couldn't find this info in the help files, etc.

I am planning on a dual monitor setup. Will version 9.04 recognise both monitors automatically and enable dual monitor features or will I need to do some more configuration? I posted about this in another thread but didn't get enough information.

[http://ubuntuforums.org/showthread.php?t=1256323](http://ubuntuforums.org/showthread.php?t=1256323)

Thanks.

---

### Post by steveneddy on 2009-09-14
Yes - please download and install a newer version.

8.10 Intrepid is also a good version and 8.04 Hardy is a Long Term Support release.

Any version from 8.04 on should detect your video card and there will be an icon on the upper tool bar that will ask you to install newer video drivers after you have completed the full installation.

It is recommended that you plug an Ethernet cable into the machine and have a full working internet connection on said cable before installation. Not necessary but it just helps things go faster after install.

Good luck. We're all counting on you.

EDIT:

The Restricted Drivers will open in a window much like this:

[IMG]http://comphobby.org/uploads/restricted_drivers_dialog.png[/IMG]

---

### Post by A Traveller on 2009-09-15
Thanks again 3rdalbum. The space bar did the trick and I now have my Ubunutu in full screen.

Hi steveneddy. Thanks for your advice. I think I already have an 8.xx version which I burned to a CD. I installed it a few weeks ago and then removed it again. I might check it out again.

My Internet is already connected via Ethernet.

I haven't even begun the learning curve for Linux yet, so I haven't a clue how to install drivers, etc, but I'll cross that hurdle after I've installed a more recent version as you have suggested.

I didn't understand what you meant by "The Restricted Drivers will open in a window much like this:"

Thanks everyone. I appreciate the help.

---

