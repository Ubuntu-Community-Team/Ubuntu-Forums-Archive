---
title: "Login Window Preferences Problem"
date: 2007-11-04
forum: Desktop Effects &amp; Customization
---

### Post by muindaur on 2007-11-04
I have a background image selected and a logo selected for the plain login manager but neither will show up. This was working previously but since I installed 7.10 as a fresh install I reverted back to 7.04 as a fresh install to see if that was the problem but it still wont show the background image for the login screen or the logo. I know it's not the format and location since I used the same ones previously. Not sure if there are any other options.

/etc/gdm/gdm.conf-custom

[daemon]
Greeter=/usr/lib/gdm/gdmlogin

[security]

[xdmcp]

[gui]
AllowGtkThemeChange=false
GtkRC=

[greeter]
UseInvisibleInEntry=true
BackgroundType=3
BackgroundImage=/home/muindaur/Images/gitsac1.jpg
LockPosition=true
Logo=/home/muindaur/Images/laughingman.JPG
DefaultWelcome=false
Welcome=Welcome to %n
BackgroundColor=#828eda
SoundOnLogin=false
ChooserButton=false
TitleBar=false
Quiver=false
Use24Clock=yes
ChooserButtonLogo=/home/muindaur/Images/laughingman.JPG

[chooser]

[debug]

[servers]

---

