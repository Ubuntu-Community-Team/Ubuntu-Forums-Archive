---
title: "xunbuntu / session stuck with xfce"
date: 2011-08-07
forum: Desktop Environments
---

### Post by geidorei on 2011-08-07
Hi - hope someone can point me in right direction here.

Old laptop, installed xubuntu - decided to have a play with xfce, and now cant change back to xubuntu desktop - logging out and changing session always comes back with xfce.

Can this be sorted or will I have to do a reinstall?

Ta folks.

---

### Post by Toz on 2011-08-07
Xubuntu _is_ xfce. What are you expecting will happen by changing sessions?

---

### Post by geidorei on 2011-08-07
Hi - ummm, right then obviously Im getting confused lol

menu at top of screen has vanished - this happened when I logged in in and changed session from xubuntu to xfce.

---

### Post by XubuRoxMySox on 2011-08-07
Xfce session is *not* the same as a Xubuntu session. Xfce is "vanilla," and Xubuntu session has all the wicked cool Xubu settings and menus and stuff.

If you have auto-login enabled, you'll always go to the default session, which apparently is "Xfce."

You can change that (in Xubuntu 10.04 - maybe different in the later versions) by going **Menu -> System -> Login Screen**, "unlock" it with your root password and select "Xubuntu Session" as default. See attached screenshot.

Let us know if that works. If it's different in your version of Xubu, say which version you're using and someone who uses that one will be along shortly I'm sure, to help you!

-Robin

---

### Post by geidorei on 2011-08-07
Hi - thats the way it is at moment, but comes up in XFCE. Ahhhhh! lol

---

### Post by geidorei on 2011-08-07
Checked /etc/gdm/custom.conf as well - and all is aok - 

AutomaticLoginEnable=false
DefaultSession=xubuntu

But, it just ignores the session and goes to xfce.

---

### Post by XubuRoxMySox on 2011-08-07
Omy... what version of Xubu are you using? Someone who is using the same one might have an answer. Wish I could help further.

But since you have auto-login disabled, you should be able to choose your session at *each* login! What happens if you log out, then log back in manually selecting Xubuntu *at login*?

-Robin

---

### Post by geidorei on 2011-08-07
Hi 11.04 - if I change session at login it ignores it and goes to xfce.

---

### Post by Toz on 2011-08-07
Do you have a .xsession, .Xsession or .xsessionrc file in your home directory? If so, what are the contents?

---

### Post by XubuRoxMySox on 2011-08-07
A wild idea, but just for fun... open Synaptic Package Manager, find xubuntu-desktop and _M_ark for Re-installation and click _A_pply.

It might be that (if you're like me) you played with stuff so much that you accidentally removed some little bit of something that Xubu session depends on.

You might get it back that way! Let us know...

-Robin

---

### Post by Toz on 2011-08-08
Just tried it now in a vm myself, and sure enough, after I log in using xfce session, I lose the xubuntu customizations even if I log back in with xubuntu-session. 

I was able to fix this by logging out, Ctrl+Alt+F1 to go to first tty, login, then execute the following command:
```
cp /etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-prechannel-xml/* ~/.config/xfce4/xfconf/xfce-prechannel-xml
```

However, I did lose my personal customizations to the interface (it was reset back to defaults).

---

### Post by geidorei on 2011-08-08
> **dixiedancer said:**
> A wild idea, but just for fun... open Synaptic Package Manager, find xubuntu-desktop and _M_ark for Re-installation and click _A_pply.

It might be that (if you're like me) you played with stuff so much that you accidentally removed some little bit of something that Xubu session depends on.

You might get it back that way! Let us know...

-Robin

Hi tried that and.... mo luck, but worth ago lol - many thanks.

---

### Post by geidorei on 2011-08-08
> **Toz said:**
> Just tried it now in a vm myself, and sure enough, after I log in using xfce session, I lose the xubuntu customizations even if I log back in with xubuntu-session. 

I was able to fix this by logging out, Ctrl+Alt+F1 to go to first tty, login, then execute the following command:
```
cp /etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-prechannel-xml/* ~/.config/xfce4/xfconf/xfce-prechannel-xml
```

However, I did lose my personal customizations to the interface (it was reset back to defaults).

Hi thanks but that didnt work either - says cp; cannot stat '/etc.....

ahhhh!

---

### Post by geidorei on 2011-08-08
> **Toz said:**
> Do you have a .xsession, .Xsession or .xsessionrc file in your home directory? If so, what are the contents?

hi - there isnt any of these files. doh!

---

### Post by Toz on 2011-08-08
What does the following return?
```
apt-cache policy xubuntu-default-settings
```
...and
```
dpkg -L xubuntu-default-settings
```

---

### Post by geidorei on 2011-08-09
Hi - as follows:

xubuntu-default-settings:
  Installed: 11.04.18
  Candidate: 11.04.18
  Version table:
 *** 11.04.18 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty/universe i386 Packages
        100 /var/lib/dpkg/status


/.
/etc
/etc/xdg
/etc/xdg/xdg-xubuntu
/etc/xdg/xdg-xubuntu/Terminal
/etc/xdg/xdg-xubuntu/Terminal/terminalrc
/etc/xdg/xdg-xubuntu/Thunar
/etc/xdg/xdg-xubuntu/Thunar/thunarrc
/etc/xdg/xdg-xubuntu/Thunar/uca.xml
/etc/xdg/xdg-xubuntu/menus
/etc/xdg/xdg-xubuntu/menus/xfce-applications.menu
/etc/xdg/xdg-xubuntu/orage
/etc/xdg/xdg-xubuntu/orage/oragerc
/etc/xdg/xdg-xubuntu/autostart
/etc/xdg/xdg-xubuntu/autostart/xfce4-tips-autostart.desktop
/etc/xdg/xdg-xubuntu/xfce4
/etc/xdg/xdg-xubuntu/xfce4/helpers.rc
/etc/xdg/xdg-xubuntu/xfce4/panel
/etc/xdg/xdg-xubuntu/xfce4/panel/default.xml
/etc/xdg/xdg-xubuntu/xfce4/panel/indicator-5.rc
/etc/xdg/xdg-xubuntu/xfce4/xfconf
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfce4-notifyd.xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfwm4.xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfce4-desktop.xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/thunar-volman.xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfprint.xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml
/etc/skel
/etc/skel/.Xdefaults
/usr
/usr/share
/usr/share/xsessions
/usr/share/xsessions/xubuntu.desktop
/usr/share/glib-2.0
/usr/share/glib-2.0/schemas
/usr/share/glib-2.0/schemas/xubuntu-default-settings.gschema.override
/usr/share/xubuntu
/usr/share/xubuntu/applications
/usr/share/xubuntu/applications/xfhelp4.desktop
/usr/share/xubuntu/applications/xfce4-terminal.desktop
/usr/share/xubuntu/applications/Thunar-bulk-rename.desktop
/usr/share/xubuntu/applications/Thunar.desktop
/usr/share/xubuntu/applications/defaults.list
/usr/share/xubuntu/session.sh
/usr/share/doc
/usr/share/doc/xubuntu-default-settings
/usr/share/doc/xubuntu-default-settings/copyright
/usr/share/doc/xubuntu-default-settings/changelog.gz
/usr/share/gconf
/usr/share/gconf/defaults
/usr/share/gconf/defaults/20_xubuntu-default-settings

Also, just noticed if say I have say a browser open and i minimize it there is no way to bring it back up - it doesnt show up as a working program on the menu.

---

### Post by Toz on 2011-08-09
> **geidorei said:**
> 
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfce4-notifyd.xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfwm4.xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfce4-desktop.xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/thunar-volman.xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfprint.xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml
/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml
Double check to see if the files are actually there:
```
ls -l /etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/*
```

If they are, then copy them over:
```
cp /etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/* ~/.config/xfce4/xfconf/xfce-perchannel-xml/
```

> Also, just noticed if say I have say a browser open and i minimize it there is no way to bring it back up - it doesnt show up as a working program on the menu.
If you've got a middle mouse button or scroll wheel, click it. Otherwise click both buttons at the same time. This will bring up a menu that lists you're running programs, see if its listed there. If it's not showing up on the panel, make sure you have the "Window Buttons" plugin enabled.

---

### Post by geidorei on 2011-08-09
Hi Toz - thanks for info re wheel, thats sorted that one.

Right then.... did an ls and no they aint there, ta for help.

---

### Post by Toz on 2011-08-09
> **geidorei said:**
> Right then.... did an ls and no they aint there, ta for help.

Then do:
```
sudo apt-get --reinstall install xubuntu-default-settings
```

I'm curious:
```
apt-cache policy xubuntu-desktop
```

---

### Post by geidorei on 2011-08-09
hi - apt-cache says


xubuntu-desktop:
  Installed: 2.128
  Candidate: 2.128
  Version table:
 *** 2.128 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) natty/universe i386 Packages
        100 /var/lib/dpkg/status

---

### Post by Toz on 2011-08-09
Did you re-install xubuntu-default-settings?
```
sudo apt-get --reinstall install xubuntu-default-settings
```

Then try the copy command:
```
cp /etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/* ~/.config/xfce4/xfconf/xfce-perchannel-xml/
```

---

### Post by geidorei on 2011-08-17
Hi - sos for delay, work, work, work lol!

Give up now - yep tried that,  going to do a reinstall. I hate bugs!

Thanks for your help.

---

