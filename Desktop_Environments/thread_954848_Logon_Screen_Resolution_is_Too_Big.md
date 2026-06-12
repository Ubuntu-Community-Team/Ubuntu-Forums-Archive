---
title: "Logon Screen Resolution is Too Big"
date: 2008-10-21
forum: Desktop Environments
---

### Post by jaie on 2008-10-21
How do you change the resolution of the gnome login screen?

I have encountered this problem on three PCs and it seems to happen after changing monitors (I think) that have different resolutions.

The logon screen where you type your username and password is the wrong resolution. The resolution of everything else though is fine, including the load screen and the Desktop.

The result is the top left section of the logon window takes up the whole screen. One was that bad we had to pick a theme that had the login buttons and username in the top left because the default theme displayed the login box as being off the screen.

---

### Post by Tamlynmac on 2008-10-21
This may help.

In the terminal:
Edit the xorg.conf file by typing : sudo gedit /etc/X11/xorg.conf

Find the section labeled "Screen"; at the bottom of that section there is a line called "Virtual" and to the right of that is a resolution setting. Change the resolution setting to the resolution you want. The resolution modes available are listed just below the virtual line.

---

### Post by jaie on 2008-10-23
I checked the xorg.conf and under Virtual I have the correct resolution, the line is shown as the following:

Virtual 1920     1200

Under Modes I have "1920x1200@60". I changed the line Virtual to 1920x2000@60 to see if it would help, but X wouldn't even load then.

When the NVidia splash screen loads it shows as the correct resolution, then the logon screen appears which has the bottom and right cropped, then once the user name and password is typed in it loads the desktop to the correct resolution.

---

### Post by amr_essam on 2008-10-24
> **jaie said:**
> I checked the xorg.conf and under Virtual I have the correct resolution, the line is shown as the following:

Virtual 1920     1200

Under Modes I have "1920x1200@60". I changed the line Virtual to 1920x2000@60 to see if it would help, but X wouldn't even load then.

When the NVidia splash screen loads it shows as the correct resolution, then the logon screen appears which has the bottom and right cropped, then once the user name and password is typed in it loads the desktop to the correct resolution.



I got the same problem here , also the splash NVIDIA appears correctly then the login window appears too large

before that i had a big problem with my nvidia fx5200 card, but it's solved , i think that nvidia is the one to blame(cant fine correct drivers)

Regards

---

### Post by jaie on 2008-10-26
I finally fixed mine by removing all information about the monitor from the xorg.conf file.

To back up my xorg.conf and reconfigure i ran:

cd /etc/X11
sudo cp xorg.conf xorg.conf.backup
sudo dpkg-reconfigure xorg-server

This removed any setting about my monitor and graphics card in the xorg.conf file. I then copied the graphics card information (Section "Device") from the old xorg.conf.backup to the new xorg.conf and it now works. I will post the resulting xorg.conf when I get to work.

---

### Post by Shazaam on 2008-10-26
If you are interested (and don't feel like using the terminal) install Startup-Manager through Synaptic. It has a section for bootup resolution.

EDIT= Ignore this as it has NO effect on the login screen.

---

### Post by null_sv on 2008-11-02
hi all!! i had that problem too even different resolutions on logon screen and desktop and it always changed it self to something different.....all i did was uninstalled and reinstalled the video driver i think is way easier than breaking you head!:guitar::lolflag::guitar::KS

---

### Post by alliance1975 on 2008-11-10
> **null_sv said:**
> hi all!! i had that problem too even different resolutions on logon screen and desktop and it always changed it self to something different.....all i did was uninstalled and reinstalled the video driver i think is way easier than breaking you head!:guitar::lolflag::guitar::KS

How do you uninstall/reinstall?

---

### Post by CLomax on 2008-11-10
Just in case someone refers to this thread I'll post my Screen section.
This is for a 1440 900 resolution:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
      SubSection "Display"
            Modes	"1440 900"
	    Virtual      1440 900
      EndSubSection
EndSection

```

---

