---
title: "Display problem with Dell 700m"
date: 2005-12-10
forum: General Help
---

### Post by Flawlessly on 2005-12-10
Hello y'all,

I'm first time here. I currently have Kubuntu & XP Pro dual boot on my Dell 700m laptop. Now that Kubuntu has set the screen to 1024x768 instead 1280x800 which is the native resolution of the screen. Anyway to change it? Thanks!

---

### Post by emperor on 2005-12-10
[quote=Flawlessly]Hello y'all,

I'm first time here. I currently have Kubuntu & XP Pro dual boot on my Dell 700m laptop. Now that Kubuntu has set the screen to 1024x768 instead 1280x800 which is the native resolution of the screen. Anyway to change it? Thanks![/quote] 

If you were using Gnome, you would check in "Preferences-Screen Resolution" and see if you can change your display to the desired resolution.
KDE in Kubuntu  also has a screen resolution control.


If not then try the following:


A simple edit to /etc/X11/xorg.conf may fix the problem.

1, First backup your xorg.conf to xorg.conf.orig

cd /etc/X11
sudo cp xorg.conf xorg.conf.orig

2. edit xorg.conf

sudo gedit xorg.conf

"Look for "Section Screen"
note Default depth size, most likely 24 bits

add "1280x800" to the beginning of the list in the xx bit "Subsection Display".

For example, here's mine:

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility M300 (M22)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1920x1200"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1920x1200"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1440x900" "1920x1200"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1440x900" "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1440x900" "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1680x1050" "1440x900" "1280x800" "1920x1200"
        EndSubSection
EndSection

3. Save the changes and exit the editor.

4. close terminal.

5. logout

6. Press "CTL-ALT-Backspace" to restart X

7. X may set your display automaticly to the new resolution or you may need to select it in "Preferences-Screen Resolution.

---

### Post by Flawlessly on 2005-12-10
OMG, in the xorg.conf has all 1280x800 all the way. I didn't even have to edit it. However, the screen is still showing 1024x768. I couldn't even adjust the resolution through desktop config. THe only one that I see is 1024x768. How weird.

---

### Post by emperor on 2005-12-10
"To get X running in 1280x800, ... install 855resolution.  Breezy users can find 855resolution in the Universe repo."

Source, see "700m" (bottom section) at: [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell]("https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell")

---

