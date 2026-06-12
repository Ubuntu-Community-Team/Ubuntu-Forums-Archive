---
title: "Problematic Xorg.conf"
date: 2009-01-19
forum: General Help
---

### Post by LequidMetal on 2009-01-19
Hi,
       I am a newbie to Linux . I had just installed Ubuntu Ibex and was trying to customise it to my preference . One of the problems i encountered was that i was unable to set my resolution to anything greater than 1024*768 using the system-->preference-->screen resolution setting ....[It was also not detecting my monitor correctly and was showing it as "unknown"].

so after going thru some threads , i opened the system-->Administration-->Nvidia xserver settings and set it to the desired res [1052*864] .It worked fine but only lasted that particular session . After a restart or shutdown it reverted back to the 1024*768 mode .

I noticed an option to overwrite [i think] the xorg.conf file in Nvidia xserver .so i went ahead and did it . 

Now my display is being detected and there are more resolutions options available in the system-->preference-->screenresolution , and am able to permanently change the  res to 1052*768 . 

BUT ! the Nvidia xserver has been disabled , along with all other desktop/window effects like the "cube  effect"   

i am also unable to open compiz  [not responding]

When i try **opening Nvidia xserver settings** i get

```
 
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

```

when i executed 
**nvidia-xconfig**

i get 

```
 
Using X configuration file: "/etc/X11/xorg.conf".

WARNING: No Layout specified, constructing implicit layout section using screen
         "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add new
         CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new
         CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.


ERROR: Unable to write to directory '/etc/X11'.


```

---

### Post by gettinoriginal on 2009-01-19
Your X11 should look like this:
```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

---

### Post by LequidMetal on 2009-01-19
xorg.conf dump

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

should i copy paste ur code in there ??

---

### Post by gettinoriginal on 2009-01-19
Just edit yours so it includes the Driver and Option

Mine:
Section "Device"
	Identifier	"Configured Video Device"
	**Driver	"nvidia"**
	**Option	"NoLogo"	"True"**
EndSection

Yours:
Section "Device"
Identifier "Configured Video Device"
EndSection

---

### Post by LequidMetal on 2009-01-19
Here s what i did

-->Opened my xorg.conf file

-->entered 
Driver "nvidia"
Option "NoLogo" "True"

-->saved

-->Tried opening the xserver settings [GUI]

Again i was told to run `nvidia-xconfig'  ...

```

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

I again opened my xorg.conf file to check it out

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

[B]Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection[/B]

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

```

....and find that the option value has vanished .... Tried again ,got the same result :(

xserver is still disabled

---

### Post by gettinoriginal on 2009-01-19
the next time you reboot, at the grub splash, hit escape, choose "try to fix X, then resume normal boot.  :P

---

### Post by LequidMetal on 2009-01-19
thanks a ton ... got it up and working !:P

but Now i am back to square one ..... i am not able to set my screen rez to anything greater than 1024*7xx 

^Well thats not exactly true ... i am able to set it to a higher rez using the Nvidia xserver ... but it only lasts this session ....next reboot it reverts back to the old 1024*7xx rez

---

### Post by RJARRRPCGP on 2009-01-19
> **LequidMetal said:**
> 
   


ERROR: Unable to write to directory '/etc/X11'.

[/code]

You must use **sudo**!

---

### Post by LequidMetal on 2009-01-19
^ i know i needed Admin privileges !  

i was using a different command

```

gksu gedit /etc/X11/xorg.conf

```

Anyway that problem is solved got a different one now ....

---

### Post by gettinoriginal on 2009-01-19
Once you change it, are you clicking "Save to Xconfig file" ??

---

### Post by LequidMetal on 2009-01-19
> **gettinoriginal said:**
> Once you change it, are you clicking "Save to Xconfig file" ??


ofcourse !

No wait

---

### Post by LequidMetal on 2009-01-19
getting this message

Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'.

have to restart to see if the change lasts

---

### Post by LequidMetal on 2009-01-19
Yeah changes to rez using the Nvidia x server settings only lasts one session

---

### Post by gettinoriginal on 2009-01-19
Once you set it under Nvidia X Server Settings, are you able to get the same thing under System > Preferences > Resolution ??

---

### Post by RJARRRPCGP on 2009-01-19
I also have to use **sudo** for the GUI Nvidia configuration, **nvidia-settings**, because if I just launch it from the
 menu, I get an error about being unable to save changes to the X configuration file, including when I want to change the resolution.

---

### Post by gettinoriginal on 2009-01-19
Yes, as the actual system file is under root permissions, but after it is set, it should stay from session to session. :confused:

---

### Post by LequidMetal on 2009-01-19
> **gettinoriginal said:**
> Once you set it under Nvidia X Server Settings, are you able to get the same thing under System > Preferences > Resolution ??

After i set it in x-server ...i get the same option under resolutions too ... I also saved it in resolution and then tried rebooting to check if the settings lasted ... it did nt ...reverts back to the default 1024*768 mode

Also the system>Preference>Resolution does not detect my monitor, shows it as "unknown"

---

### Post by gettinoriginal on 2009-01-19
Yeah, mine says unknown also, but it's working, so it has nothing to do with the resolution.  Does it recognize your monitor in NvidiaX Server Settings ??

---

### Post by LequidMetal on 2009-01-19
yeah it does

---

### Post by LequidMetal on 2009-01-19
i searched a few threads , there were some that said that i should find an entry for screen rez and refresh rate in the xorg.conf file which i can edit .... I couldnt find any in mine :confused: ...any ideas?

After messing up my xorg.conf once already i really dont want to try out anything on my own , so would really appreciate some guidance here :(

---

### Post by gettinoriginal on 2009-01-19
That was before 8.10, the developers are working to do away with Xorg, so it is no longer possible to do that.  Try this when you are in session with the correct resolution.
go to applications>accessories>terminal. type in: ```
sudo dpkg-reconfigure -phigh xserver-xorg
```  then reboot.
On reboot, a box may come up asking you to select your monitor and graphics card. If you do get that option, don't try "test".  After logging in, we hope it will save.

---

### Post by LequidMetal on 2009-01-20
Followed the above 

changes after reboot

-->Screen refresh rate changed and stayed to the value i set before rebooting

-->Screen rez back to the default 1024*768 value

-->Most importantly my Nvidia driver has again been disabled .... :(

---

### Post by gettinoriginal on 2009-01-20
Well, I hate to say this, but I am out of ideas.  I would suggest that you start a new thread (different title) as we are on page 3, and those tend to get ignored.  I would suggest "Resolution not saving to new session"  Again, I am sorry we could not get it resolved.  :(

---

### Post by LequidMetal on 2009-01-24
solved my problem ... 

Changes using the The x-server lasted only oe session ...... so i simply copied the code from the "save changes to xserver config file>Preview" window


Opened the xorg.conf in GUI mode .... 

paste>save file .... thats it ..... now the changes have been made permanent and everything else is working fine :D

---

