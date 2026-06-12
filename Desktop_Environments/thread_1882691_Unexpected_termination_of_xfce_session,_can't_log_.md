---
title: "Unexpected termination of xfce session, can't log back in"
date: 2011-11-17
forum: Desktop Environments
---

### Post by tjfitz on 2011-11-17
What do I do now to get my desktop back?  Today I was playing around with "Appearance" and "Window Manager" themes.  I was going down the list of window manager themes (via the down arrow), so I could see how each looked.  As I was near the bottom of the list, the whole X/desktop session suddenly died, kicked me back to the screen you see during boot-up before GDM starts, then after a second or so, GDM restarted.  I try to log in again, but it just did the same thing: session died, back to the boot screen, then GDM restarted.

Before this happened, I had installed xpad and had set it up like I wanted, but I noticed a lot of disk activity and graphics lag whenever I'd move or resize one of the notes.  I thought that might have been the culprit, so I moved all the xpad dotfiles onto my desktop and used apt-get to uninstall xpad.

That didn't help, so my only guess now is that something went wrong in the window manager because I was jumping through themes so quickly.  Help!

FYI, my machine is an IBM T42.

---

### Post by tjfitz on 2011-11-17
I have some more information that I thought might be pertinent.  At the gdm login screen, if I choose an openbox session, I can log in without getting kicked out.  I'm going to guess that that means something is wrong with xfce or xfwm specifically and not with xorg or gdm.

---

### Post by Toz on 2011-11-17
If you're using 10.04, I believe one of the themes had a bug in it that made xfce crash. You may have located that theme. If you can log in via openbox, then edit the file **~/.config/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml** and near the beginning, change the line that reads:
>     <property name="ThemeName" type="string" value="BADTHEME"/>

...(BADTHEME will actually display the name of the theme that is causing the problems)

to:
```
    <property name="ThemeName" type="string" value="Default"/>

```

Then try logging in again.

---

### Post by tjfitz on 2011-11-17
Thanks for your help!

> **Toz said:**
> If you're using 10.04, I believe one of the themes had a bug in it that made xfce crash. You may have located that theme. If you can log in via openbox, then edit the file **~/.config/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml** and near the beginning, change the line that reads:

...(BADTHEME will actually display the name of the theme that is causing the problems)

to:
```
    <property name="ThemeName" type="string" value="Default"/>

```

Then try logging in again.

I did the edit as instructed.  The first line I came to like that had "DarkLooks" as the theme, so I changed it to "Default".  I got the same behavior.  I just checked xsettings.xml to be sure that it actually changed, and it was as it should be:

```
<?xml version="1.0" encoding="UTF-8"?>

<channel name="xsettings" version="1.0">
  <property name="Net" type="empty">
    <property name="ThemeName" type="string" value="Default"/>
    <property name="IconThemeName" type="string" value="gnome"/>
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
    <property name="Antialias" type="int" value="-1"/>
    <property name="Hinting" type="int" value="-1"/>
    <property name="HintStyle" type="string" value="hintfull"/>
    <property name="RGBA" type="string" value="none"/>
  </property>
  <property name="Gtk" type="empty">
    <property name="CursorThemeName" type="string" value="default"/>

    <property name="CursorThemeSize" type="int" value="0"/>
    <property name="CanChangeAccels" type="bool" value="false"/>
    <property name="ColorPalette" type="string" value="black:white:gray50:red:purple:blue:light blue:green:yellow:orange:lavender:brown:goldenrod4:dodger blue:pink:light green:gray10:gray30:gray75:gray90"/>
    <property name="FontName" type="string" value="Sans 9"/>
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
```
I think you are going in the right direction.  It makes sense to me that it has something to do with a theme judging by the circumstances.  Are there other config files I can check?  What if the WM has already designated the "bad theme" as the "Default" theme?

---

### Post by tjfitz on 2011-11-17
I have another thought to add.  "DarkLooks" is an "Appearance" theme.  I had chosen DarkLooks as my appearance theme, but when the crash happened, I was switching through the different window manager themes.  I don't remember which WM theme I was on at the time because it crashed so suddenly.  Could the WM theme have been the culprit?  Where would I look to edit the config file for this?

---

### Post by tjfitz on 2011-11-17
On a hunch, I decided to start clearing out the dotfiles in ~/.config/xfce4/xfconf/xfce-perchannel-xml/.

I moved xsettings.xml to xsettings.xml.old and that didn't help.  Then I moved xfwm4.xml to xfwm4.xml.old, and that fixed it.

To see what went wrong, I went to the xfce settings control panel > window manager and started seeing what happened with the different themes (and I made sure my appearance theme was different in case there was a nasty interaction involved).  When I selected the theme "Wildbush" I got the same crash.  So there's something wrong with the Wildbush theme, but apparently the Darklooks theme is fine.

What can I do to disable, remove, or fix the faulty theme so I don't accidently get this again?

---

### Post by Toz on 2011-11-17
Yes, now I remember, it was the Wildbush window theme. If you go to /usr/share/themes, you should see a directory called Wildbush (or wildbush - not sure of the capitalization). Just delete the directory. You will need root access.

That being the case, you can go to your backup xfwm4.xml file, change the Wildbush entry to Default, and move those files back to get your customizations back.

---

### Post by tjfitz on 2011-11-17
Thanks so much for your help. My old xsessions.xml file was already overwritten, but customizations are easy enough, so no problem there.

---

