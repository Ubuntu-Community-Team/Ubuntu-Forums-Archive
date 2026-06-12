---
title: "Enabling higher resolutions?"
date: 2006-01-11
forum: Desktop Environments
---

### Post by DaveChakrabarti on 2006-01-11
Just did a new Ubuntu install (complete linux newbie) and only have 640 x 480 and 800 x 600 available as screen resolutions. The video card (radeon) is being detected properly, and i enabled one higher resolution during the installation process, which resulted in a black screen...it was too high for the monitor (I think it was 1600 x 1200). 

I fixed it by doing this as sudo:

dpkg-reconfigure xserver-xorg

...and running through all of those options. I also tried:

gconf-editor

...since that was suggested as a possible solution, but couldn't figure out where to make changes / edits. 

No matter what I try, I can't get it to show me anything other than those two desktop resolutions when I try to change it in the gui. I even went through the xerver-xorg reconfig again, and verified that it's showing 1024 x 768 as an option (the current highest resolution).

Suggestions / ideas?

Thanks,

  Dave.

---

### Post by Thirsteh on 2006-01-11
Look in your X.org config file.

sudo gedit /etc/X11/xorg.conf

There's a section with resolutions and refresh rates. Check if there's anything unusual there, or something missing.

---

### Post by 23meg on 2006-01-11
Check out the instructions in [this thread]("http://www.ubuntuforums.org/showthread.php?t=83973").

---

### Post by Karst on 2006-01-11
The problem is likely in the /etc/X11/xorg.conf file.  Before you mess with it, you  should make a backup..
cd /etc/X11
sudo cp xorg.conf xorg.conf.bak

Then edit the xorg.cof file.

vi xorg.conf    (use whatever editor you're comfortable with)

Search for the words "Default Screen"  Here's what it looks like on mine:

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82852/855GM Integrated Graphics Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24

The 'Screen' subsections follow this entry.  Each has a depth.  Here's mine at depth 24 (default depth)

        SubSection "Display"
                Depth           24
                Modes           "1024x768"
                Virtual         1152 864
        EndSubSection

(The 'Virtual line is one I added so I can pan over a larger virtual screen)
The 'Modes' line shows the modes available.  My laptop doesn't look good on anything but 1023x768 so I took out the "420x640" entry and it doesn't try to do that resolution any more.  You might try adding the resolution you like on the 'Modes' line -- just leave a space and add it on.  The older X configuration files requred some timing information for the modes, I don't see it in the xorg.conf file so it may not be necessary now.

---

