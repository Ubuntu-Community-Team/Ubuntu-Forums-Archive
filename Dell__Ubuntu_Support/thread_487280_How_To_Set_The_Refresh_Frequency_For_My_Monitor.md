---
title: "How To Set The Refresh Frequency For My Monitor?"
date: 2007-06-28
forum: Dell  Ubuntu Support
---

### Post by weverjames on 2007-06-28
I JUST MANAGED TO CHANGE THE MONITOR RESOLUTION TO THE NATIVE 1680X1050.
FOR THAT I HAD TO ADD IT USING THE TERMINAL.  HOWEVER THE REFRESHING FREQUENCY IS STILL UNDER THE RECOMMENDED 60 Hz.  CURRENTLY IS USING THE DEFAULT 54 Hz AND SOMETIMES THE MONITOR DOES A FUNNY NOISE WHEN CHANGING WINDOWS.  
COULD SOMEONE WATCH MY CONFIGURATION AND TELL ME WHAT TO DO?
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       31-82
        Vertrefresh     56-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation GeForce 7300 LE"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes   "1680x1050" "1024x768"  "800x600"  "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
 Modes   "1680x1050" "1024x768"  "800x600"  "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes   "1680x1050" "1024x768"  "800x600"  "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes   "1680x1050" "1024x768"  "800x600"  "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes   "1680x1050" "1024x768"  "800x600"  "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes   "1680x1050" "1024x768"  "800x600"  "640x480"
        EndSubSection

---

### Post by weverjames on 2007-06-28
thanks for the help.   I am overwhelmed with so much information.

---

### Post by neptho on 2007-06-28
In your above, do the Horizontal and Vertical refreshes actually match the capability of your monitor?  You should be able to look up the specifications on your monitor, somewhere (usually in the booklet accompanying, and online) will have it listed.

---

### Post by weverjames on 2007-06-30
I already changed the frequency ib the previous configuration.  However, in the  screen resolution,  only appear the 2 default refreshing rates of 50 and 54.  According to the manufacturer (Nec) the monitor should be set to work at 60.  Currently I chose the 54 but I need to change to 60.  Although I put the frequencies specified in the monitor manual, the only 2 options are 50 and 54.
Can anyone help me.
Other problem is that when a go to the I can not save any modification ( I could the first time, but not anymore).  How can I do?

---

### Post by weverjames on 2007-06-30
Come on guys, help me.
This is the only issue I have and I will be a completely happy converter.
I hope there is a generous bright mind out there who could help me.

---

### Post by fjgaude on 2007-06-30
I have a feeling your monitor is running at 60 Hz. Turn the monitor off with the computer still on and see what it says when it comes back on.

My monitor says 60 Hz while the Ubuntu Screen Resolution menu says 50 Hz.

frank

---

### Post by chriswyatt on 2007-07-01
This needs to be fixed in a later release.  I remember having to force Beryl to use 60 Hz otherwise it would run at 50 Hz and be out-of-sync with my monitor.

---

### Post by royg on 2007-07-01
Helo there James,

You aren't the only one with this problem, I used to suffer from it too, even if you change xorg.conf your monitor would simply stay the same,

this is what eventually worked for me (single monitor not for dual monitors) a simple act actually 

goto 
System -> Preferences -> Screen resolution (then simply restart your gdm) (read below before you try this)

if that is not there or it fail to restart your gdm, use the termnal and type 
xrandr  (depending on your configuration you may need to type  sudo xrandr)

hope it will help, 
cheers
royg

---

