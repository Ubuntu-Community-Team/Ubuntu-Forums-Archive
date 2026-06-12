---
title: "E520N display resolution"
date: 2007-06-19
forum: Dell  Ubuntu Support
---

### Post by lahook on 2007-06-19
I just got my e520n today and everything is fine, except I can't change the resolution to 1680x1050.
I have the monitor connected to both of my Ubuntu computers. On the old computer I had no problem changing the resolution. The Dell I haven't been able to.
sudo dpkg-reconfigure -phigh xserver-xorg worked on the old one,not on the Dell

I added 1680x1050 to /etc/X11/xorg.conf manually
The dell has the integrated Intel 82G965 graphics.
Does the Dell use a different file for the monitor settings?
Any suggestions?

---

### Post by nikjoshi on 2007-06-19
I have a similar problem and hence wanted to continue the thread rather than create a new one.  I have a new E520N and the display cannot be changed to 1680x1050.  I have a Dell 19" LCD monitor and an NVIDIA GEFORCE 7300LE graphics card.  Any help will really be appreciated as the  current display seems to take me to neanderthal times! ;)

---

### Post by avik on 2007-06-19
Can either of you post the "Screen" section of the file /etc/X11/xorg.conf?

---

### Post by lahook on 2007-06-19
here's mine:
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82G965 Integrated Graphics Controller"
	Monitor		"DELL E228WFP"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

anything wrong here?

---

### Post by avik on 2007-06-19
Well, the right resolution is present, so you should in theory be able to switch to that resolution.  What exactly are you doing to try to change resolutions?  Is it not changing, or is it giving some error?

---

### Post by lahook on 2007-06-19
system>preferences>Screen Resolution

1680x1050 is not in the list
there's only 6 choices 1280x768  1024x768  800x600  640x480  1280x800 and 1280x1280

when I did "sudo dpkg-reconfigure -phigh xserver-xorg" the screen never came up to select the driver and the resolutions

---

### Post by nikjoshi on 2007-06-19
For my system it shows:
Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation GeForce 7300 LE"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
EndSection

---

### Post by nikjoshi on 2007-06-19
Actually in my case, the system is not even recognizing the monitor which is a Dell SE198WFPV monitor and I have used the digital video connection between the monitor and the display card...

---

### Post by nikjoshi on 2007-06-19
(and here is where my true naivity in using Linux shows) I used gksu nvidia-settings and I was able to change everything...

Thanks a lot for the fast responses though - enjoyed thoroughly!!!

---

### Post by lahook on 2007-06-19
lahook@dell:~$ sudo dpkg-reconfigure -phigh xserver-xorg
Password:

The screen flashed and came back and gave the following warning


xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070619215321
lahook@dell:~$

---

### Post by avik on 2007-06-20
lahook,

Is your resolution showing up in System->Preferences->Screen Resolution?  You have the right resolution in you xorg.conf file, so Ubuntu should recognize it.

---

### Post by lahook on 2007-06-20
> **avik said:**
> lahook,

Is your resolution showing up in System->Preferences->Screen Resolution?  You have the right resolution in you xorg.conf file, so Ubuntu should recognize it.

It's not a choice on the drop down menu. I'm wondering if it uses that /etc/X11/xorg.conf file or a different one. I've looked through all the xorg.conf file and haven't found one that matches the "System>Preferences>Screen Resolution" choices.
I would think the integrated graphics would support that resolution.

---

### Post by sacherjj on 2007-06-27
I'm a newbie with Ubuntu, but I was able to get 1680x1050 and 1280x1024 dual setup with my 520N with 7300 card.  I just pieced together commands from various threads on here.

Disconnected DVI (1680x1050) and left only the 1280x1024 as RGB

Backup xorg.conf: (just in case)
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

```

Make a clean file:
```

sudo dpkg-reconfigure xserver-xorg

```

You will have to answer a few questions here.  Take your time and read what is asked and it is pretty easy.

Plug in DVI cable and configure with the nVidia-settings:
```

gksudo nvidia-settings

```

Setup as Twin-View.  The only problems I had were forgetting to save the settings out to xorg.conf.  And then I forgot to delete old settings groups.  I forget what they were called, but they are available in the Advanced... view.  I deleted every one but the 1680x1050 +0 +0 1280x1024 +1680 +13 setting.

Now after rebooting, I get both monitors set correctly.  It should be a little easier to use nvidia-settings to work with just the single 1680x1050.  I also setup a button on the top toolbar for "gksudo nvidia-settings" so I can quickly go into it to change things.  Need to learn how to add it to the menu instead.

Hope that helps someone.

Edit: Forgot to mention that this is with enabling the binary driver.  I forget what that is called (Restricted Drivers) or something like that.  I'm on my WinXP box at work, so I can't check.

---

