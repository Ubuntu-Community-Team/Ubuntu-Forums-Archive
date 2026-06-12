---
title: "Theme: &quot;Make Default&quot;?"
date: 2011-03-18
forum: Desktop Environments
---

### Post by jorge@jorgepadron.com on 2011-03-18
On a brand new fresh Ubuntu Desktop 10.10 installation, I go to...

*System > Preferences > Appearance > Theme [Tab] > Customize... [Button] > Window Border [Tab]*

...and select a different window border (i.e. "Simple"). All my desktop window borders change to "Simple" as expected. My question is: How do I make this modified theme the "default" theme for the entire computer + for all new user accounts and for the login screen? Unfortunately, the *Preferences > Appearance* application does not have a "Make Default" button like the *Preferences > Monitors* and *Preferences > Power Management* applications.

Thank you in advance,

Jorge Padron

---

### Post by Frogs Hair on 2011-03-18
I'm not sure if you can make it default , but a start would be to use the save as tab and name the theme. The new users would have the ability to change themes anyway unless you were planning on instructing them not to.

---

### Post by Krytarik on 2011-03-19
Try this:
- press Alt+F2
- enter "gconf-editor"
- browse to "/apps/metacity/general/theme"
- right-click at it
- click at "Set as Default"

Greetings.

---

### Post by jorge@jorgepadron.com on 2011-03-19
> **Krytarik said:**
> Try this:
- press Alt+F2
- enter "gconf-editor"
- browse to "/apps/metacity/general/theme"
- right-click at it
- click at "Set as Default"

Greetings.

[Krytarik]("http://ubuntuforums.org/member.php?u=1187548"), I have a couple of questions if you don't mind, regarding themes on Ubuntu 10.10:

. If I save my current theme as default with gconf-editor, does it mean that new user accounts that I create from now on will have "my theme" instead of the Ubuntu defualt theme?

. Do you know if it is possible to change the tooltip shape of the Ubuntu login window to square instead of round corners? How do I change the default login window theme?

Thank you again for your help!!! 

Jorge

---

### Post by Krytarik on 2011-03-19
> **jorge@jorgepadron.com said:**
> 
. If I save my current theme as default with gconf-editor, does it mean that new user accounts that I create from now on will have "my theme" instead of the Ubuntu defualt theme?

Yes, given that the theme is system-wide installed, in "/usr/share/themes".
FYI, this is the key for the GTK theme ("Controls"): "/desktop/gnome/interface/gtk_theme"
> **jorge@jorgepadron.com said:**
> 
. Do you know if it is possible to change the tooltip shape of the Ubuntu login window to square instead of round corners? How do I change the default login window theme?

Please see the first part of my earlier post:
[http://ubuntuforums.org/showthread.php?p=10468340](http://ubuntuforums.org/showthread.php?p=10468340)

Regarding the tooltips: This depends on the chosen theme, whether it uses the "new tooltip style" or not.

---

### Post by jorge@jorgepadron.com on 2011-03-19
> **Krytarik said:**
> Yes, given that the theme is system-wide installed, in "/usr/share/themes".
FYI, this is the key for the GTK theme ("Controls"): "/desktop/gnome/interface/gtk_theme"

Please see the first part of my earlier post:
[http://ubuntuforums.org/showthread.php?p=10468340](http://ubuntuforums.org/showthread.php?p=10468340)

Regarding the tooltips: This depends on the chosen theme, whether it uses the "new tooltip style" or not.


Krytarik, THANK YOU!!!

---

### Post by Krytarik on 2011-03-19
> **jorge@jorgepadron.com said:**
> Krytarik, THANK YOU!!!
You're welcome!

PS: You should do something about your member name!
I'm sure the admins would allow to change it: [http://ubuntuforums.org/sendmessage.php](http://ubuntuforums.org/sendmessage.php)

---

### Post by kerke on 2011-03-21
PS: You should do something about your member name!
I'm sure the admins would allow to change it: [http://ubuntuforums.org/sendmessage.php](http://ubuntuforums.org/sendmessage.php)

---

### Post by Krytarik on 2011-03-21
All these settings use different Gconf keys:

GTK theme -> "/desktop/gnome/interface/gtk_theme"
colors -> "/desktop/gnome/interface/gtk_color_scheme"
window borders -> "/apps/metacity/general/theme"
background image -> "/desktop/gnome/background/picture_filename" and other associated ones

---

### Post by kerke on 2011-03-21
> **Krytarik said:**
> All these settings use different Gconf keys:

GTK theme -> "/desktop/gnome/interface/gtk_theme"
colors -> "/desktop/gnome/interface/gtk_color_scheme"
window borders -> "/apps/metacity/general/theme"
background image -> "/desktop/gnome/background/picture_filename" and other associated ones

Krytarik, these are the gconf-editor settings I "set as default" based on your advice. I added a couple (button_layout and icon_theme)"

[FONT=Courier New][SIZE=2][COLOR=#000000][FONT=Arial]window borders: /apps/metacity/general/theme[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]button_layout: /apps/metacity/general/button_layout[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]gtk_theme: /desktop/gnome/interface/gtk_theme[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]icon_theme: /desktop/gnome/interface/icon_theme[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
background: /desktop/gnome/background/picture_filename[/FONT][/COLOR][/SIZE][/FONT]

The "colors -> "/desktop/gnome/interface/gtk_color_scheme" was not available under gconf-editor.

Now all users have the same default theme.

Thank you

---

### Post by Krytarik on 2011-03-21
> **kerke said:**
> 
The "colors -> "/desktop/gnome/interface/gtk_color_scheme" was not available under gconf-editor.

Then you didn't specify custom colors for the chosen GTK theme.

You're welcome, again! ;-)

---

### Post by kerke on 2011-03-25
> **Krytarik said:**
> Then you didn't specify custom colors for the chosen GTK theme.

You're welcome, again! ;-)

[Krytarik]("http://ubuntuforums.org/member.php?u=1187548"), if on a fresh Ubuntu 10.10 installation, I change the default theme Window Border (System > Preferences > Appearance > Theme [tab] > Customize [button] > Window Border [tab]) to "Simple" -- Now my desktop theme is the default Ubuntu theme but with a different window border. What is the gconf-editor key I need look for to "Set as Default" my window border? The only thing I want to set as default is the current Window Border.

---

### Post by Krytarik on 2011-03-25
> **Krytarik said:**
> All these settings use different Gconf keys:

GTK theme -> "/desktop/gnome/interface/gtk_theme"
colors -> "/desktop/gnome/interface/gtk_color_scheme"
[B]window borders -> "/apps/metacity/general/theme"
[/B]background image -> "/desktop/gnome/background/picture_filename" and other associated ones
;-)

---

### Post by kerke on 2011-03-25
> **Krytarik said:**
> ;-)

It worked OK on my home laptop, I don't know why it didn't work on my work test computer.

Thank you!

---

### Post by Krytarik on 2011-03-25
> **kerke said:**
> It worked OK on my home laptop, I don't know why it didn't work on my work test computer.

Please post back, after another try.

---

