---
title: "HOWTO: Configuring LXDE for Ubuntu"
date: 2012-01-06
forum: Desktop Environments
---

### Post by Emblem Parade on 2012-01-06
If you're fed up with the recent "innovation" and bloat in desktop environments (Unity, GNOME 3, KDE, and even XFCE), then LXDE is for you.

One option is to use Lubuntu, but some of us prefer to work with the standard Ubuntu install, and possibly add LXDE as an alternate desktop, while still enjoying Ubuntu features like the global menu, indicators and notification. Unfortunately, the default LXDE configuration in Ubuntu is ... sad. This guide will help you create a nice LXDE desktop in standard Ubuntu that is as close to the standard Ubuntu experience as possible. It will only take a few minutes and do nothing irreversible.

This guide was tested with Ubuntu 11.10. Here's a screenshot of the result:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210544[/IMG]

**Step 1: Installation**

First, let's install LXDE. These packages will give you only the essentials without any bloat:

```
sudo apt-get install lxde-core lxappearance obmenu qt4-qtconfig xcompmgr
```

Next, let's add the [Ambiance and Radiance themes for LXDE]("http://gnome-look.org/content/show.php/Ambiance+%26+Radiance+Themes+for+Xfce%2BLXDE?content=146674") by RAVEfinity:

```
cd ~
wget "http://gnome-look.org/CONTENT/content-files/146674-Ambiance&Radiance-XfceLXDE-11-10-2.tar.gz"
sudo tar xzvf "146674-Ambiance&Radiance-XfceLXDE-11-10-2.tar.gz"
sudo mv Ambiance-Xfce-LXDE /usr/share/themes/
sudo mv Radiance-Xfce-LXDE /usr/share/themes/
rm "146674-Ambiance&Radiance-XfceLXDE-11-10-2.tar.gz"
```

**Step 2: Configuring the appearance**

Logout, and login with the LXDE session. Yay! Well, except for the fact that it's ugly. :)

Go to "Preferences" -> "Openbox Configuration Manager". (Openbox is your window manager. It draws the window decorations.)

1. In "Theme", select "Ambiance-Xfce-LXDE" (or the Radiance version). Note that the window decorations are not *exactly* like those in Compiz or even Metacity, due to the limitations of Openbox. But it's not bad!
2. In "Appearance", set the button order of "Window Titles" to "CIML".
3. Change all the fonts to the "Ubuntu" font, "Regular" style.

Now go to "Preferences" -> "Customize Look and Feel". (This affects all LXDE components. Note that LXDE uses GTK+2, and is comptable with any GTK+2 theme.)

1. In "Widget", choose "Ambiance" (or Radiance), and set the default font to "Ubuntu" font, "Regular" style.
2. In "Icon Theme", choose "Ubuntu-Mono-Dark" (or "Light" for Radiance).
3. In "Font", you really want to enable antialising, and likely hinting, too. (Note: I had to fool around with these settings a bit to get them to work properly. It seems a little buggy.)

Now go to "Preferences" -> "Qt 4 Settings" -> "Appearance" and change the "GUI Style" to GTK+. This will make sure Qt applications have the same theme you chose before.

Now we'll enable some pretty compositing (transparencies, fades and shadows) using Cairo:

```
gksudo gedit /etc/xdg/lxsession/LXDE/autostart
```

Add this line to the top:

```
@xcompmgr -fF -I-.002 -O-.003 -D1 -cC -t-5 -l-6 -r5
```

Save, logout and login to see all your changes.

*Troubleshooting 1: Compositing*

If you get weird graphical glitches, it's best to replace the line above with minimal compositing using this instead:

```
@xcompmgr -n
```

*Troubleshooting 2: Font size issues*

On some machines, fonts may appear to be far too big or far too small. This is because X11 is not configured for the right DPI (dots-per-inch). The following my help: 

```
gksudo gedit /etc/X11/xorg.conf
```

You should see a block called 'Section "Monitor"'. Make sure it has the following line:

```
Option "DPI" "96 x 96"
```

Logout and login for changes to take effect. If this doesn't solve things for you, you'll need to delve a bit deeper into your X11 configurtion. Good luck!

*Troubleshooting 3: Multiple monitor setups*

The LXDE panel will appear on the primary monitor. However, if the primary monitor is *not* the leftmost monitor, the panel size will be incorrect. Luckily, this is easy to fix. Right-click on the panel and choose "Panel Settings". Under "Geometry" -> "Margin" put the sum width in pixels of all monitors to the left of your primary monitor. In my case, I had one monitor on the left that was 1680 pixels wide, so I just had to put "1680".

*Troubleshooting 4: The default browser has been changed to Chrome instead of Firefox*

Easy to change back:

```
sudo update-alternatives --config x-www-browser
```

**Step 3: Configuring the keyboard**

LXDE does not do any special handling of the keybord, leaving it to you your windows manager to X11.

To configure keyboard layouts, we'll use X11. In this exmple we'll enable ALT+CAPSLOCK for switching between English/USA and Hebrew/Israel layouts, as well as enable right-CTRL for the compose key:

```
gedit ~/.config/lxsession/LXDE/autostart
```

Add these to the file (it may be empty):

```
@setxkbmap -option grp:alt_caps_toggle "us,il"
@setxkbmap -option "compose:rctrl"
```

Settings will take effect next time you login. You can also test the commands immediately by running them in the terminal (without the "@" prefix).

For variations, you'll need to explore setxkbmap.

Keyboard shortcuts are handled by Openbox, our window manager. You can edit them manually using [this guide]("http://openbox.org/wiki/Help:Bindings"):

```
gedit ~/.config/openbox/lxde-rc.xml
```

(There's a program called [obkey]("http://code.google.com/p/obkey/") that can help, but it's not packaged for Ubuntu.)

Some suggested changes to keyboard bindings:

1. Replace references to "lxterminal" with "x-terminal-emulator". This will make sure that you run your default terminal emulator.
2. Replace reference to "pcmanfm" with "nautilus" if you prefer it (see below).
3. If you want to assign a key to your web browser, use "x-www-browser", which will open whatever is configured as your default.

**Enhancement 1: Replace PCManFM with Nautilus**

You might like PCManFM managing your desktop, but it was too minimal for my tastes. (It also does a bad job with wallpapers on multiple monitor setups.) To use Nautilus instead:

```
gksudo gedit /etc/xdg/lxsession/LXDE/autostart
```

Comment out the pcmanfm line by prefixing a "#" to it, and add a line for Nautilus. In my case it looked like this:

```

#@pcmanfm --desktop --profile LXDE
@nautilus --no-default-window
```

You will need to logout and login for the changes to take effect.

You'll likely also want to change the keybinding for PCManFM to lacunh Nautilus instead (see above).

**Enhancement 2: Add the Unity Panel**

For some users, the Panel may already be working for you. If not, then run:

```
gnome-session-properties
```

Click "Add" and call the new entry "Unity 2D Panel" with the command "unity-2d-panel". Make sure the entry is enabled.

Next time you login, you should see the Unity panel, providing you with the global menu as well as the rest of the Unity indicators. You might want to remove some applets from the LXDE panel (clock, etc.) because they already have equivalents in the Unity panel.

*Known Issues:*

1. The Unity panel's "Logout" option in the power indicator will not work. But LXDE's shutdown app works fine.
2. The global menu) will only appear in the primary workspace.

**Enhancement 3: Synapse**

Synapse is a lean-and-mean keyboard launcher that fits perfectly with LXDE's lightweight profile:

```
sudo apt-get install synapse
```

---

### Post by MG&amp;TL on 2012-01-06
Brilliant guide, although the TODO will be nice too.

---

### Post by Emblem Parade on 2012-01-06
Thanks! Added, plus an option for changing the default browser back to Firefox. :)

---

### Post by Jan-A6VMX on 2012-10-01
The version of the Ambiance and Radiance themes is not suited for Ubuntu 12.04, because that contains a newer Gnome version. You could get (near-)white text on a very light background, when you are using the well known Gnome tools.

See [http://xubuntugeek.blogspot.nl/2012/06/how-to-install-ambiance-and-radiance.html]("http://xubuntugeek.blogspot.nl/2012/06/how-to-install-ambiance-and-radiance.html") for a howto about obtaining and installing Ambiance and Radiance Themes.

---

### Post by vanlong441 on 2012-11-02
[SIZE=3]This guide is particularly for customizing [COLOR=Blue]Lubuntu 12.04[/COLOR][/SIZE]


[COLOR=Red]Update 6 Nov 2012[/COLOR]

Install the latest PCManFM (default file manager in Lubuntu)

```
sudo add-apt-repository ppa:lubuntu-dev/lubuntu-daily && sudo apt-get update
```

Then open synaptic and upgrade only PCManFM. I cannot test all other updates from the repo for lxpanel, lxsession, and such. Therefore, you should be responsible for any manual upgrade other than PCManFM. You can purge the ppa or synaptic >> settings >> repositories >> other software >> uncheck or delete lubuntu-daily ppa.


[COLOR=Red]Update 5 Nov 2012[/COLOR][INDENT] Current version of Xcompmgr in 12.04 is not drawing shadow below windows and menus. The suggestion is to  remove xcompmgr if you have had it installed, download and install this older version.

32bit [http://archive.ubuntu.com/ubuntu/pool/universe/x/xcompmgr/xcompmgr_1.1.5-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/x/xcompmgr/xcompmgr_1.1.5-1_i386.deb)
64bit [http://archive.ubuntu.com/ubuntu/pool/universe/x/xcompmgr/xcompmgr_1.1.5-1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/x/xcompmgr/xcompmgr_1.1.5-1_amd64.deb)
[/INDENT]-------------------------------[INDENT]Xcompmgr like any other compositing managers leads to tearing. The solution is to turn it off when you are watching videos, and turn it back on when you need it. This can be done with key-bindings.

```
sudo leafpad ~/.config/openbox/lubuntu-rc.xml
```Scroll down to line 179, add these lines under [COLOR=DarkGreen]<keyboard>[/COLOR]. You can change the keys with your own. Log out and log back. Now anytime you press Super + C, Xcompmgr is turned on and Shift + Super + C, Xcompmgr is turned off. Please consult [_this guide_]("http://www.lubuntutips.com/2012/05/lubuntu-hotkeys-keybindings.html") for a better understanding of key-binding in LXDE.

> [COLOR=DarkGreen]<keyboard>[/COLOR]
    <chainQuitKey>C-g</chainQuitKey>
    <!-- Keybindings for composite switching -->
    <keybind key="**W-c**">
      <action name="Execute">
        <command>xcompmgr -fF -I-.002 -O-.003 -D1 -cC -t-5 -l-6 -r5</command>
      </action>
    </keybind>
    <keybind key="**W-S-c"**>
      <action name="Execute">
        <command>killall xcompmgr</command>
      </action>
    </keybind>[/INDENT]=============================================

Final results can be found here [http://ubuntuforums.org/showpost.php?p=12327879&postcount=1](http://ubuntuforums.org/showpost.php?p=12327879&postcount=1)

```
sudo add-apt-repository ppa:nilarimogard/webupd8
```Appmenu, window title, window buttons, indicators, chameleon notification

```
sudo apt-get install gnome-panel maximus appmenu-gtk appmenu-gtk3 appmenu-qt firefox-globalmenu lo-menubar indicator-applet-appmenu indicator-appmenu indicator-appmenu-gtk2 gnome-window-applets indicator-applet-complete notify-osd pidgin-libnotify xcompmgr

gconftool-2 --set /apps/maximus/no_maximize --type=bool true

sudo apt-get remove notification-daemon

gnome-panel
```Win + Alt + right click to work with panels and panel applets until you have something similar to [_this_]("http://i.imgur.com/bU92V.png").

For Shutdown button >> Add to panel >> Custom Application Launcher[INDENT]Type: Application
Name: Shutdown
Command: lubuntu-logout
Icon: /usr/share/icons/elementary-mono-dark/panel/24/system-shutdown-panel.svg
[/INDENT]**[SIZE=3]Auto startup[/SIZE]**

In Desktop session settings (found in Preferences), enable only [_these_]("http://i.imgur.com/lbZjk.png").

Edit /etc/xdg/lxsession/Lubuntu/autostart with your favorite text editor as Root (In pcmanfm >> tools >> open current folder as root). You can use mine.

# means disabled
@ means added to startup
For xcompmgr, use *@xcompmgr -n* if you have trouble with graphics.
Conky can be found here [http://hfcf.deviantart.com/art/Conky-Cronograph-Station-278646771](http://hfcf.deviantart.com/art/Conky-Cronograph-Station-278646771)
> 
#@lxpanel --profile Lubuntu
@conky -c $HOME/.Conky/cronograph/conkyrc
@xscreensaver -no-splash
@xfce4-power-manager
@pcmanfm --desktop --profile lubuntu
@/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
@gnome-panel
@maximus
@xcompmgr -fF -I-.002 -O-.003 -D1 -cC -t-5 -l-6 -r5Now log out and log back.

**[SIZE=3]Other tips:[/SIZE]**

Disable "Fast user switching" with Ubuntu Tweak >> Tweak >> Miscellaneous
Install pavucontrol to modify sound settings

---

### Post by TREESofRIGHTEOUSNESS on 2012-11-23
This is my fix for the Openbox window buttons.  I tried to make it look identical to the ambiance theme, though I couldn't make only the close button orange....  anyhow it looks nice with circle buttons

---

