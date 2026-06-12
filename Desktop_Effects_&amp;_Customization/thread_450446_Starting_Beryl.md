---
title: "Starting Beryl"
date: 2007-05-21
forum: Desktop Effects &amp; Customization
---

### Post by ddollas on 2007-05-21
I just can't seem to make Beryl run, I have a RV350 Radeon 9550 video card, I have everything installed, I can access the management settings, and emerald theme settings.  Just nothing ever seems to happen.  Beryl works fine if I place knoppix in my machine and tell it to use Beryl so I'm fairly certain I can run it, I just don't know what I'm doing wrong, any help would be wonderful in this matter. :).

---

### Post by Ub1476 on 2007-05-21
Well, I guess KNOPPIX fixes everything for you, right? And if it don't work when you "fix it" manually, as you do on Ubuntu, there is something you are doing wrong:p

Have you installed XGL or AIGXL?

Do you log into correct session?

Check in gnome session (default):

```
 glxinfo | grep direct
```

Should turn out like: direct rendering: Yes

If direct rendering was "No", then you need to install drivers for your graphic card. For the session thing, I heard that AIGXL isn't so bad for the ATI 900 series, but XGL gives better 3d maybe a little slower performance, but but..

Good link here, both for XGL and AIGXL: [Linky]("http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29")

If you gonna follow this guide remove beryl first (just to do it clean):

```
sudo aptitude remove beryl beryl-core beryl-manager beryl-plugins beryl-plugin-data beryl-settings beryl-setting-bindings libberyldecoration0 libberylsettings0 libemeraldengine0
```

Hope you find out of it:)

---

### Post by ddollas on 2007-05-21
Ok, I'm going to try that guide, however a side problem has come up for me.  I tried some other guide namely this one.  [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

In doing so I broke xserver for awhile, managed to get it back, but I can't get my resoultion to go over 1000x700 or something like that.  I'm afraid to touch anything in config files because I'm just plain stupid when I do so.  Any suggestions?

---

### Post by Ub1476 on 2007-05-21
The reason for you not to get your resolution higher is because your graphics driver isn't installed. 

If you know they are then write in terminal:

```
sudo gedit /etc/X11/xorg.conf
```

and add your resolution in the "Screen" section.

If you want a clean xorg.conf file you can write:

```
sudo dpkg-reconfigure xserver-xorg
```

Wouldn't use the last code if aren't a pro on computers though..

Anyway, if you are following the closed source drivers (XGL) then you are installing the graphic drivers from "Restricted Drivers Managers" so don't worry about looking for that. I guess you install graphic drivers in the AIGXL guide too, but I haven't used it so I don't know:p

Oh, and you are installing AIGXL in the guide you previous used, so I guess you have already tried that. To remove AIGXL: 
```
udo aptitude remove xserver-aigxl
```

But, well I'm not sure about that code so it might be you just get errors, like can't find AIGXL etc.

You kinda edit the xorg.conf file when using that guide, so it isn't odd you broke it:)

---

### Post by ddollas on 2007-05-21
I know, I knew i shouldn't have bothered to try that one and should have waited for a forum response.  Do you happen to know if there is a way to detect my settings automatically like when it was first installed?  I detected and enabled my video card drivers via the restricted drivers manager, however it still won't let me get all the resolutions I used to have, only the first three, anything else if I try to configure with the second option you gave me results in something being totally unreadable and a basically melted screen.  :(

---

### Post by Gus_T_Reer on 2007-05-21
Can I suggest if you currently have a working xorg.conf file that you make a copy of it before you do any messing around. You should then be able to restore it if things get a little messy.
cd /etc/X11
sudo cp xorg.conf myxorgbackup.conf

Then to restore
cd /etc/X11
sudo cp myxorgbackup.conf xorg.conf

You will probably need to reboot to let it take effect.

As regards to other (older) xorg.conf files have a look in /etc/X11 and see if there are any files called xorg.conf.2007nnnnn as these will have been created when some changes have been made. If you look at these you might be able to spot one that you know would work (but remember to backup your current xorg.conf first).

Without wishing to hijack the thread I'd like to ask, while the topic has been mentioned, is it possible to have XGL and direct rendering at the same time. I have an x850xt with the restricted driver that normally gives direct rendering but as soon as I specify that I want to use XGL the direct rendering switches off with the message Xlib:  extension "XFree86-DRI" missing on display ":1.0". I thought it was a given that XGL switched off direct rendering?

---

### Post by ddollas on 2007-05-21
Well, one reinstall later and I have beryl working...  thanks for you help, and I will certainly be backing up any file that I intend to mess around with in the future.

---

### Post by Ub1476 on 2007-05-21
> Do you happen to know if there is a way to detect my settings automatically like when it was first installed?

Yes, when you use this code:

```
sudo dpkg-reconfigure xserver-xorg
```

You will be asked question about your computer, and when finished, xorg.conf should be clean and nice like your first one.:)

> Without wishing to hijack the thread I'd like to ask, while the topic has been mentioned, is it possible to have XGL and direct rendering at the same time. I have an x850xt with the restricted driver that normally gives direct rendering but as soon as I specify that I want to use XGL the direct rendering switches off with the message Xlib: extension "XFree86-DRI" missing on display ":1.0". I thought it was a given that XGL switched off direct rendering?

I get the same message in console when I'm logged in in XGL

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No

```

Still Beryl and everything else is working, so no need to worry, I think:p

---

### Post by Gus_T_Reer on 2007-05-21
Ok, thanks Ub.

---

### Post by ddollas on 2007-05-21
OK One last question and I think I'll be done, how does one use emerald to change the theme of Beryl without breaking the beryl install?  (my video card doesn't like it if i mess with too much it seems, though I did get it working fine again)

---

### Post by Gus_T_Reer on 2007-05-21
The actual applying of Emerald themes appears to have been broken a while back. Assuming you now have the red beryl icon you have to select Emerald Theme Manager, click on the theme you want and then right-click on the beryl icon and select Reload Window Decorator to have the selected theme applied. It's messy I'm afraid.

---

### Post by ddollas on 2007-05-21
that it kinda messy, but thanks!

---

