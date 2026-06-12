---
title: "Font rendering in xfce"
date: 2012-04-19
forum: Desktop Environments
---

### Post by tivatranquio on 2012-04-19
Hi, I'm trying Xubuntu 12.04 beta 2, it is not bad, but I don't like the font rendering.
In ubuntu 10.10 the fonts looks great! How can i use the gnome/ubuntu font rendering in Xubuntu?

---

### Post by theos911 on 2012-04-19
I have been putting serious work into making Xubuntu 12.04 look exactly like Ubuntu Classic. I'll give you just the font changes that I made since you aren't looking for the complete overhaul I did.

Settings --> Settings Manager --> Appearance --> Font Tab
*Change default font to Ubuntu 11
*Enable anti-aliasing
*I prefer 96 DPI. (You may prefer something different.)


Settings --> Settings Manager --> Window Manager --> Style Tab
*Change title font to Ubuntu Bold 11


I hope this helps. Enjoy!

---

### Post by tivatranquio on 2012-04-19
I have already tried those step, but the font looks different! It looks "wider" in xfce..

---

### Post by theos911 on 2012-04-19
You can try enabling hinting. I don't really like it, but it does seem to make them skinnier.

(@school atm so can't check, but I *think* hinting is the right option)

---

### Post by tivatranquio on 2012-04-20
i have tried everything, I think I need to patch libcairo2 or something like this..

---

### Post by tivatranquio on 2012-04-20
Solved: [http://noz3001.wordpress.com/2011/07/01/ubuntu-font-rendering-on-debian-wheezy/](http://noz3001.wordpress.com/2011/07/01/ubuntu-font-rendering-on-debian-wheezy/)

---

### Post by neu5eeCh on 2012-05-04
> **tivatranquio said:**
> Solved: [http://noz3001.wordpress.com/2011/07/01/ubuntu-font-rendering-on-debian-wheezy/](http://noz3001.wordpress.com/2011/07/01/ubuntu-font-rendering-on-debian-wheezy/)

I tried this, but the font rendering still looks washed out in Xubuntu 12.04. _Pretty bad_ compared to Unity, and this is a fresh install of Xubuntu, not the "desktop" on top of Unity. I don't get it.

---

### Post by neu5eeCh on 2012-05-04
Well... I've solved part of it by copying over the contents of the etc/fonts/* directory from an 11.04 Xubuntu install on a separate partition. However, font rendering remains in serious need of font smoothing. Any ideas? Anti-aliasing only gets me half-way there.

Also, I installed the Unity desktop via terminal, as a hail-mary, but the option to start up unity doesn't appear in the Xubuntu "greeter" - is it GDM now? What's up with **that**? How do I fix it?

---

### Post by Toz on 2012-05-04
> **VTPoet said:**
> Also, I installed the Unity desktop via terminal, as a hail-mary, but the option to start up unity doesn't appear in the Xubuntu "greeter" - is it GDM now? What's up with **that**? How do I fix it?

Xubuntu uses lightdm now as well. You need to have a desktop file in /usr/share/xsessions for an option to appear at login. According to my ubuntu precise install in virtualbox, there is an ubuntu.desktop file there with the following contents:
```

[Desktop Entry]
Name=Ubuntu
Comment=This session logs you into Ubuntu
Exec=gnome-session --session=ubuntu
TryExec=unity
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-3.0
```

Try creating that file and restarting lightdm to see if it shows up.

---

### Post by mips on 2012-05-04
> **VTPoet said:**
> Well... I've solved part of it by copying over the contents of the etc/fonts/* directory from an 11.04 Xubuntu install on a separate partition.

Maybe someone running Ubuntu 12.04 could archive and upload their /etc/fonts folder to the net for others to inspect/copy.

---

### Post by neu5eeCh on 2012-05-05
> **Toz said:**
> Xubuntu uses lightdm now as well. You need to have a desktop file in /usr/share/xsessions for an option to appear at login. 

Thanks Toz. I installed Unity rather than the Ubuntu-Desktop. Doh! :rolleyes:

However, I still haven't gotten fonts to look as good as in Unity. They're acceptable, but in need of smoothing. I can't find an option for smoothing in XFCE.

Also, as an unrelated aside, have you tried the XFCE global menu in 12.04? The errors are above my pay grade:

-- The following packages have unmet dependencies:
-- xfce4-appmenu-plugin :
-- Depends: libindicator6 (>= 0.3.90) but it is not installable
-- Recommends: appmenu-gtk2 but it is not installable
-- E: Unable to correct problems, you have held broken packages.

But I thought I'd check with you, O grand wizard of XFCE.

---

### Post by The Cog on 2012-05-05
> I can't find an option for smoothing in XFCE.
In Applications, Settings, Settings Manager, Appearance, Fonts. You probably want to enable antialiasing, and try out different levels of hinting. Beware that although most windows take on the new fonts immediately, Firefox seems to need restarting.

---

### Post by Toz on 2012-05-05
> **VTPoet said:**
> Also, as an unrelated aside, have you tried the XFCE global menu in 12.04? The errors are above my pay grade:

-- The following packages have unmet dependencies:
-- xfce4-appmenu-plugin :
-- Depends: libindicator6 (>= 0.3.90) but it is not installable
-- Recommends: appmenu-gtk2 but it is not installable
-- E: Unable to correct problems, you have held broken packages.

But I thought I'd check with you, O grand wizard of XFCE.

If you're using the ppa:the-warl0ck-1989/xfce-appmenu-plugin PPA, then have a look at this bug report: [https://bugs.launchpad.net/xfce4-appmenu-plugin/+bug/922615]("https://bugs.launchpad.net/xfce4-appmenu-plugin/+bug/922615").

If you still want to use it, looks like right now you need to download the code, make some edits, and build it manually. Or wait for the author to fix it.

---

### Post by neu5eeCh on 2012-05-05
> **The Cog said:**
> In Applications, Settings, Settings Manager, Appearance, Fonts. You probably want to enable antialiasing, and try out different levels of hinting. Beware that although most windows take on the new fonts immediately, Firefox seems to need restarting.

Thanks Cog. I've already tweaked and twiddled those knobs and dials. I filed a bug with the XFCE devs, but they marked the bug invalid, saying font rendition has to do with the distros, not XFCE. Fair enough; but poor font rendition has turned a lot of users off of XFCE, fair or not. Right now, I'm in Unity rather than Xubuntu because I can't handle the lack of smoothing in FF, LibreOffice, and the whole DE in general.

Is there a third party app that I could install in Xubuntu to manage system-wide font settings?

---

### Post by Toz on 2012-05-05
@VTPoet, can you post back the following:

- the contents of ~/.config/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml

and the results of:
```
apt-cache policy xubuntu-default-settings
apt-cache policy ttf-droid
apt-cache policy dconf-gsettings-backend
apt-cache policy gconf2
```

---

### Post by neu5eeCh on 2012-05-05
Where I really notice the poor font smoothing is when using apps like browsers, e-mail apps and libreoffice (basically anything where there's text). When booting up the Ubuntu-Desktop, the font smoothing in any of these apps is beautiful. It's night and day. I would post images but they never really demonstrate the difference.

--------
<?xml version="1.0" encoding="UTF-8"?> 

<channel name="xsettings" version="1.0">
  <property name="Net" type="empty">
    <property name="ThemeName" type="string" value="Ambiance-Voyager-Dark"/>
    <property name="IconThemeName" type="string" value="F-Dark-Withe"/>
    <property name="DoubleClickTime" type="int" value="250"/>
    <property name="DoubleClickDistance" type="int" value="5"/>
    <property name="DndDragThreshold" type="int" value="8"/>
    <property name="CursorBlink" type="bool" value="true"/>
    <property name="CursorBlinkTime" type="int" value="1200"/>
    <property name="SoundThemeName" type="string" value="default"/>
    <property name="EnableEventSounds" type="bool" value="false"/>
    <property name="EnableInputFeedbackSounds" type="bool" value="false"/>
  </property>
  <property name="Xft" type="empty">
    <property name="DPI" type="empty"/>
    <property name="Antialias" type="int" value="1"/>
    <property name="Hinting" type="int" value="-1"/>
    <property name="HintStyle" type="string" value="hintslight"/>
    <property name="RGBA" type="string" value="none"/>
    <property name="Lcdfilter" type="string" value="lcdnone"/>
  </property>
  <property name="Gtk" type="empty">
    <property name="CursorThemeName" type="string" value=""/>
    <property name="CursorThemeSize" type="int" value="0"/>
    <property name="FontName" type="string" value="Ubuntu 10"/>
    <property name="CanChangeAccels" type="bool" value="false"/>
    <property name="ColorPalette" type="string" value="black:white:gray50:red:purple:blue:light blue:green:yellow:orange:lavender:brown:goldenrod4:dodger blue:pink:light green:gray10:gray30:gray75:gray90"/>
    <property name="IconSizes" type="string" value=""/>
    <property name="KeyThemeName" type="string" value=""/>
    <property name="ToolbarStyle" type="string" value="icons"/>
    <property name="ToolbarIconSize" type="int" value="3"/>
    <property name="IMPreeditStyle" type="string" value=""/>
    <property name="IMStatusStyle" type="string" value=""/>
    <property name="MenuImages" type="bool" value="true"/>
    <property name="ButtonImages" type="bool" value="true"/>
    <property name="MenuBarAccel" type="string" value="F10"/>
    <property name="IMModule" type="string" value=""/>
  </property>
</channel>
-------
apt-cache policy xubuntu-default-settings
xubuntu-default-settings:
  Installed: 12.04.11
  Candidate: 12.04.11
  Version table:
 *** 12.04.11 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe i386 Packages
        100 /var/lib/dpkg/status
-----

apt-cache policy ttf-droid
ttf-droid:
  Installed: 20101110+git-2
  Candidate: 20101110+git-2
  Version table:
 *** 20101110+git-2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe i386 Packages
        100 /var/lib/dpkg/status
-----
apt-cache policy dconf-gsettings-backend
dconf-gsettings-backend:
  Installed: 0.12.0-0ubuntu1
  Candidate: 0.12.0-0ubuntu1
  Version table:
 *** 0.12.0-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main i386 Packages
        100 /var/lib/dpkg/status
------
apt-cache policy gconf2
gconf2:
  Installed: 3.2.5-0ubuntu2
  Candidate: 3.2.5-0ubuntu2
  Version table:
 *** 3.2.5-0ubuntu2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main i386 Packages
        100 /var/lib/dpkg/status

---

### Post by mr_pouit on 2012-05-05
> **VTPoet said:**
> 
    <property name="Lcdfilter" type="string" value="lcdnone"/>


Did you try other values: "lcddefault" (that's probably the one you want), "lcdlight", and "lcdlegacy"? Either use xfconf-query or logout and edit manually the xml file.

(you should probably set rgba to something else too, "none" isn't usually great, unless you're using an old crt screen)

---

### Post by neu5eeCh on 2012-05-05
> **mr_pouit said:**
> Did you try other values: "lcddefault" (that's probably the one you want), "lcdlight", and "lcdlegacy"? Either use xfconf-query or logout and edit manually the xml file.

(you should probably set rgba to something else too, "none" isn't usually great, unless you're using an old crt screen)

Thanks. Bumping up the DPI definitely helped with the menus. 

I twiddled with that already but apparently wasn't aggressive enough. Adjusting the lcd defaults didn't make any difference one way or the other. I set rgba to none. Using any of the four configurations turned text documents into rainbows.

The problem of smoothing remains in text applications like Libre, Gimp, Scribus, Firefox, Chrome, etc... If I could bring XFCE's standards up to Unity's, I'd have this licked.

---

### Post by Toz on 2012-05-05
The Xfce default xsettings file (/etc/xdg/xfce4/xfconf/xfce-perchannel-xml) is as such:
```
<?xml version="1.0" encoding="UTF-8"?>

<channel name="xsettings" version="1.0">
  <property name="Net" type="empty">
    <property name="ThemeName" type="string" value="Xfce"/>
    <property name="IconThemeName" type="string" value="Tango"/>
  </property>
  <property name="Xft" type="empty">
    <property name="DPI" type="int" value="-1"/>
  </property>
</channel>
```

The default xubuntu xsettings file (/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml) is as such:
```
<?xml version="1.0" encoding="UTF-8"?>

<channel name="xsettings" version="1.0">
  <property name="Net" type="empty">
    <property name="ThemeName" type="string" value="greybird"/>
    <property name="IconThemeName" type="string" value="elementaryXubuntu"/>
  </property>
  <property name="Xft" type="empty">
    <property name="DPI" type="int" value="96"/>
    <property name="Antialias" type="int" value="1"/>
    <property name="Hinting" type="int" value="-1"/>
    <property name="HintStyle" type="string" value="hintslight"/>
    <property name="RGBA" type="string" value="rgb"/>
  </property>
  <property name="Gtk" type="empty">
    <property name="CursorThemeName" type="string" value="Human"/>
    <property name="CursorThemeSize" type="int" value="24"/>
    <property name="FontName" type="string" value="Droid Sans 10"/>
  </property>
</channel>
```

Maybe, as a test, try creating a new user account and before logging in as the new user, copying over /etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml to the new users .config/xfce4/xfconf/xfce-perchannel-xml/ directory and see if it makes a difference.

---

### Post by neu5eeCh on 2012-05-05
OK. By Gad! Just to prove I'm not making this up, observe *la difference*:

**Xubuntu**

[IMG]http://poemshape.files.wordpress.com/2012/05/xubuntu.png[/IMG]

Now notice, in Ubuntu, how much sharper the W and V are, and how much less fuzz there is around the un-bolded fonts:

**Ubuntu**

[IMG]http://poemshape.files.wordpress.com/2012/05/ubuntu.png[/IMG]

These are both on the same install, same Firefox, same fonts.

**Edit: **What's more, I'm writing this in Xubuntu and the png of the Ubuntu font looks as clean as if it were in Ubuntu.

---

### Post by Toz on 2012-05-05
Yeah, I was going to say that the xubuntu one looks clearer to me.

---

### Post by neu5eeCh on 2012-05-05
> **Toz said:**
> Yeah, I was going to say that the xubuntu one looks clearer to me.

Really? The difference, to me, is stark.

---

### Post by neu5eeCh on 2012-05-05
Well... I don't get it... but... I rebooted, logged into Ubuntu, twiddled and tweaked, returned to Xubuntu, turned on RGB and this time, with maybe *just* the right DPI setting, *just* the right hinting, and with LCD set to default, and then rebooting, I've gotten Xubuntu to look as good as Ubuntu.

Case closed. Phew.:rolleyes:

If this were my thread, I would mark it solved. You're a saint, Toz, for putting up with me.

---

### Post by brainwash on 2012-05-05
Firefox does not care about the XFCE font smoothing settings and XFCE simply does not sync the various configurations (xsettings, fontconfig, Xdefaults/Xresources).

In my opinion, font rendering in Firefox looks the best, if you switch to **hintfull** and **lcdlegacy**.

---

### Post by astef on 2013-03-21
> **VTPoet said:**
> Thanks Cog. I've already tweaked and twiddled those knobs and dials. I filed a bug with the XFCE devs, but they marked the bug invalid, saying font rendition has to do with the distros, not XFCE. Fair enough; but poor font rendition has turned a lot of users off of XFCE, fair or not. Right now, I'm in Unity rather than Xubuntu because I can't handle the lack of smoothing in FF, LibreOffice, and the whole DE in general.

I second that. The font rendering is a pain in Xubuntu (for me the only one so far, otherwise great distro).

Changing the font to "Ubuntu 11" and using a custom DPI (108) seems to help though (Settings->Settings Manager->Appearance->Fonts)...

Sorry for bringing up an old thread.

---

