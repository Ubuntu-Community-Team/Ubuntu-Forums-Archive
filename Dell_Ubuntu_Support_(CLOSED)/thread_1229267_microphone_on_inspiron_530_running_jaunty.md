---
title: "microphone on inspiron 530 running jaunty"
date: 2009-08-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by motoperpetuo on 2009-08-01
i've got a logitech headset that i'm ultimately hoping to use for skype. however, i can't get the microphone to work. 

i've tried both alsamixer and gnome-volume-control from a terminal, and everything there seems to be enabled and unmuted, with the volume turned up. still, if i open sound recorder (from the applications|sound & video menu) and make a recording, it won't play my voice back.

has anyone been able to get sound recording to work on an inspiron 530 with jaunty? it's one of the machines that came preinstalled with ubuntu, i think with hardy (i've since wiped the hard drive and installed jaunty). seems like this shouldn't be too hard, but i can't think of anything else to try to get it working.

also, i should add that the headphones work fine. i can play music or any other type of sound through them on this computer with no problems.

---

### Post by motoperpetuo on 2009-08-02
I finally got it to work. Here are the steps I took to make my microphone work on my Dell Inspiron 530 in Ubuntu 9.04. Keep in mind that I was just fiddling, and I'm not sure I have everything I did in here, or that all these steps are actually necessary:

1)Installed PulseAudio applet: sudo apt-get install gnome-volume-control-pulse

2)Reboot.
3)After rebooting, there should now be two sound applets on the upper-right. If you mouse over one of them, it will say something like “Output: 71%”. I think this is the one that controls the mike.
4)Right-click on the appropriate sound applet and choose “Sound Preferences.”
5)Click on the Input tab. Note the name of the device selected for sound input (I only had one listed, “HDA Intel – ALC888 Analog.”
6)Close Sound Preferences.
7)Now right-click on the other sound applet and choose Preferences.
8\)The Volume Control Preferences dialog appears. Open the drop-down menu and look for the device you found in step 5. Choose that device and close the dialog.
9)Right click the sound applet (the one you clicked in step 7) and choose Open Volume Control.
10)Click on the Preferences button at the bottom of the Volume Control dialog. A dialog called Volume Control Preferences appears.
11)Select all the available options in Volume Control Preferences and close this dialog.
12)Back in the Volume Control dialog, click the Recording tab. If any devices are disabled here (indicated by a red x over the device), click on them to enable them.
13)Click on the Options tab. You should see two Input Source values here. If you're plugging your headset into the front microphone jack, set both of these to “Front Mic.” I would assume that you can use “Mic” if you're using the jack in the back.

I think that's all I did. It definitely works now. Ubuntu has come a long way since I first attempted to use it eight years ago. Hopefully configuring a microphone is something that will become easier in the future...this was tough to figure out, and I'm not 100% I could do it again if I had to.

I hope this is still working tomorrow!!! (Sometimes things I fix end up breaking themselves again in a day or so...frustrating.)

---

