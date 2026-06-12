---
title: "Understanding my nvidia 9.10 and ubuntu stuff.."
date: 2009-12-16
forum: Desktop Environments
---

### Post by phony on 2009-12-16
First of all, I'm really new, so please bare with me.

I requested a ubuntu desktop edition 9.10 disc and it recently arrived, I tryed the no install trial from the disc and than installed from there, it apparently is the karmic 32bit version as shown in "system monitor". Now I had no preference and just wanted any OS, but I do have 4gb of ram. Would the 64 bit version be on the disc to and I  could have installed it different?

Next question, **MOST IMPORTANTLY**, I heard that versions 190 of nvidia drivers had sliders that fix overscan easily. I'm using a GTS250 with my SXRD projection tv and I need this badly... So, like a goofball, I inserted the ppa for karmic from this strange website into the terminal and unknowingly downloaded all the driver info that got me to 190.42. However, I cannot see that anything has changed in the Nvidia X Server besides the new number. Anyone willing to explain where, when, how a slider is located? I'm thinking of taking these [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978) instruction and going through the setup again, but if I saw some solid evidence of a easy overscan fix existing it would certainly raise my morale.

I really appreciate it, I feel everything is so close to perfection, besides the not knowing stuff so good.:-|

---

### Post by steveneddy on 2009-12-16
You may get some help with some of your issues by looking at the links in my sig.

Also is you aren't sure about the legitimacy of the web site you are installing software from, don't install software from there.

Ubuntu is very secure, as long as the end user only installs softre from trusted sources.

Regarding your nvidia driver issue, look in 

**System --> Administration --> Hardware Driver**s

and make sure that you have the driver that you want to use checked and that you have pushed the **Activate** button.

The restart X by

Ctrl+Alt+Backspace

and see if that make any difference.

---

### Post by phony on 2009-12-16
I only have 1 driver listed "Nvidia accelerated graphic driver(version 190)" and it is activated green next to it, if that is what that combo was supposed to do. I didn't notice a change. Here is where I got the ppa, 
[http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)

I guess the website is pretty legit, but have you heard of a slider to gain access to with this driver, I'd love some instructions to get to the blessed overscan fixing slider. Assuming karmic supported it.

---

### Post by steveneddy on 2009-12-16
```
sudo apt-get install nvidia-settings
```

You will find this tool after install in Administration.

---

### Post by phony on 2009-12-16
Would that be "Nvidia X Server Settings" under administration? I've been pressing all the buttons in there for awhile, but it looks exactly the same as when I had 185 driver. No, overscan quick fix that I'm hopeful for... I cut and pasted the code in the terminal to see what it did and got the following.

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

---

### Post by phony on 2009-12-16
I'd really be thankful, if someone could just tell me if the disc I got "9.10 desktop edition"(is it too vague?) had a 64bit version on it and whether these new nvidia drivers will fix the overscan on my HDTV using said disc's OS. Otherwise, I could spend days researching something that doesn't exist...

---

### Post by realzippy on 2009-12-16
SXRD tv?which resolution do you want?Not available in nvidia-settings?
What "overscan slider" ?

Generally take the 190.42 driver.Don't know what your CD contains....


Edit:

[http://ubuntuforums.org/showpost.php?p=8448626&postcount=1127](http://ubuntuforums.org/showpost.php?p=8448626&postcount=1127)

from the thread you posted.Maybe it refers to the 195 Driver..?So you could download it from this strange website:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
and install it this way (you might know):
[http://ubuntuforums.org/showpost.php?p=6235436&postcount=1](http://ubuntuforums.org/showpost.php?p=6235436&postcount=1)
(type *kde stop* instead of *gdm stop*)

---

### Post by phony on 2009-12-16
The TV is a KDSA3000 3LCD rear projection, the last of its kind... I want 1080p scaled down to a visable resolution when in normal mode. I just expected a slider that fixes overscan to magically appear in the nvidia X server settings gui after I installed the drivers... That is what I heard.

And I think my issue may relate to others here on ubuntu using karmic, because when I type nvidia-settings in the terminal I get...
```
ERROR: Unable to assign attribute CursorShadow specified on line 21 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 22 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 23 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 24 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 25 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 26 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 27 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 28 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 29 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 30 of configuration
       file '/home/j/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 31 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 32 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 33 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 34 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 35 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppEnhanced specified on line 36 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 37 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 38 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 39 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 40 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 41 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 42 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 43 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 44 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 45 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 46 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GPUScaling specified on line 47 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureBrightness specified on line 48
       of configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureContrast specified on line 49 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureHue specified on line 50 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSaturation specified on line 51
       of configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       52 of configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 53 of
       configuration file '/home/j/.nvidia-settings-rc' (no Display
       connection).


```So, does the solution to my problems not exist? As for the cd I got, it came in a orange sleeve if that helps...

---

### Post by phony on 2009-12-16
Turns out I went into synaptics package manager, and did a search for "NV 190" and downloaded/installed "nvidia-settings-190"... It gave me the slider in nvidia xserver settings, and now my screen is overscan free. Nice.

Although, it uninstalled nvidia-settings, that had some undernote about Canonical support until 2010, I guess I can kiss that goodbye.

Now, I'd just like to know if I should reinstall ubuntu, is it likely the CD I have also has a 64bit version on it?

---

### Post by steveneddy on 2009-12-17
> **phony said:**
> Turns out I went into synaptics package manager, and did a search for "NV 190" and downloaded/installed "nvidia-settings-190"... It gave me the slider in nvidia xserver settings, and now my screen is overscan free. Nice.

Although, it uninstalled nvidia-settings, that had some undernote about Canonical support until 2010, I guess I can kiss that goodbye.

Now, I'd just like to know if I should reinstall ubuntu, is it likely the CD I have also has a 64bit version on it?

Glad you got that issue resolved.

About the 64 bit version, unless the CD states that it is actually a 64 bit version then it is 32 bit.

You can DL the 64 bit version or simply order a new 64 bit CD.

In terminal type

```
uname -m
```

to see it you already have 64 bit installed.

64 bit output will display as

```
x86_64
```

---

