---
title: "no desktop settings with right click (or else) . . ."
date: 2012-01-13
forum: Desktop Environments
---

### Post by Farinet on 2012-01-13
I'm running lubuntu 11.10 on a netbook. When i'm right clicking on the desktop in the menu there is no desktop setting (and, there is also missing comparing to a Powermac i've running LXDE under wheezy, the pcmanfm option).

When i'm running in a terminal 'pcmanfm -desktop-pref' the desktop settings appear.

Which prefs/confs should i change to have the desktop settings (and, if possible, the pcmanfm) with the right click on the desktop?

TIA

---

### Post by Farinet on 2012-01-13
Ok, answering to myself: 

I went to:

```
/etc/xdg/openbox/menu.xml
```and added (as root) the following lines:

  ```
<item label="Desktop Settings">
    <action name="Execute"><execute>pcmanfm --desktop-pref</execute></action>
</item>
```All fine now. I don't remember, i changed that settings ever. So, i guess, the missing desktop settings it's by lubuntu default (?)

---

### Post by Rodney9 on 2012-01-13
Well done fixing it yourself.


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by Farinet on 2012-01-13
Thanks for the link, Rodney!

---

### Post by Guilden_NL on 2012-01-20
For all of you who prefer to work in a GUI environment here's a way to do this with only one terminal command to install the app.

[LIST=1]
[*]Download LXMenu Editor  [http://lxmed.sourceforge.net/]("http://lxmed.sourceforge.net/")
[*]Install LXMenu Editor [http://lxmed.sourceforge.net/help.html#install]("http://lxmed.sourceforge.net/help.html#install")
[*]Add a New Item to Preferences to Allow Wallpaper Changes
[/LIST] Click on **Preferences Menu**, then add **New Item**. Name it whatever you want, then add this for Command:  *pcmanfm --desktop-pref*   
Don't forget to add an icon image that you would like to associate with it.

No more command line when you want to change the wallpaper or change the text on the Desktop!



[IMG]http://lxmed.sourceforge.net/images/screen1.jpg[/IMG]

---

### Post by Rodney9 on 2012-01-21
To change the background I now use this -

[Lubuntu Wallpaper Changer]("http://ubuntuforums.org/showthread.php?t=1843824")

Thanks to Gaygerbil

---

