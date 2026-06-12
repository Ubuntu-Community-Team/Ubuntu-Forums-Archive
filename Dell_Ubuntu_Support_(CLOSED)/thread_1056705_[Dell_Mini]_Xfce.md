---
title: "[Dell Mini] Xfce?"
date: 2009-02-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by stopie on 2009-02-01
With the mini, Im rollin just regular Ubuntu 8.10. I was wondering if anyone had comparative experience on the mini with gnome vs xfce. Specifically if xfce is any faster than gnome of the mini. I use it for school and interwebs so there is an emphasis on light, and Ive heard good things about the speed of xfce so I was just wondering...I prefer gnome, so Im not looking for the usual flameage of whats better, just needto know whats the fastest.

Regards,
Stopie

---

### Post by anjilslaire on 2009-02-01
I tried Xubuntu on my Mini (havee it on my desktop) and it just didn't seem to go well on the 1024x600 screen, Everything just seemed so big, and buttons, etc were offscreen.

Loaded Ubuntu 8.10 (gnome) plus the Netbook Remix, runs great.

---

### Post by vegetarianshrimp on 2009-02-01
[http://mydellmini.com/forum/xubuntu-on-the-mini-9--t232.html](http://mydellmini.com/forum/xubuntu-on-the-mini-9--t232.html)

---

### Post by iggykoopa on 2009-02-01
I'd recommend crunchbang linux, it's what I'm running now. It's based on ubuntu but uses openbox for the window manager, pretty snappy on the mini. Here's the link [http://crunchbanglinux.org/](http://crunchbanglinux.org/) , If you check in the forums there there are some guidelines on setting it up to use screen realestate best on a netbook.

---

### Post by stopie on 2009-02-01
Conclusion of usage of both is below \/  \/  \/

---

### Post by stopie on 2009-02-02
Xubuntu is nice, it was faster than ubuntu and somehow fit on the screen just fine. Text was a bit large though. It had a nice comfortable feel, so I think it will be my safe room if I decide to go back to "straight" ubuntu. 

Im using Crashbang now, and its super nice. Its quick and minimal. Openbox is super functional, and thus far everything has worked out of the box, and the package manager makes it super versitile with an easy trasnfer from ubuntu.

I think I can see myself using this one for awhile, if not, it will deffinitly be xubuntu instead of ubuntu.

Thanks again for the help guys and gals.

---

### Post by ugm6hr on 2009-07-17
> **stopie said:**
> Text was a bit large though.

I found this too irritating... So found the solution (for 9.04 Jaunty):

For Menu text size:
Menu -> Settings -> Appearance
Fonts tab
Change "Default Font" to "Sans 8"

For Desktop text size:
Menu -> Settings -> Desktop
Icons tab
Use Custom Font Size 6 (tick box)

For Thunar (File Manager):
```
nano ~/.gtkrc-2.0
```
Or replace nano with chosen editor (e.g. mousepad or gedit)
```
style "fonttweak"
{
font_name="Sans 6"
}

widget_class "*Thunar*View*" style "fonttweak"

```
Save and exit

The log out and log back in again, and everything should fit more pleasantly on the screen.  Feel free to use alternatives to 8 and 6 font sizes chosen here (the XFCE default is 9).

One other thing is the lack of keyboard volume control keys.  I actually installed xfce4 to the 9.04 NBR, and was surprised that the Volume Control was not a default, so:
```
sudo apt-get install xfce4 xfce4-mixer
```
Added that to the panel a la Gnome too.

Then:
Menu -> Settings -> Keyboard
Application Shortcuts tab
Click Add
**amixer set Master 2+**
Click OK
Press Fn+6
Repeat above for
**amixer set Master 2- ** (Fn+5)
**amixer set Master toggle ** (Fn+4)

You don't get the nice GUI control for keyboard volume control popping up as in Gnome, but it works as expected.  Interestingly, it appears to recognise when my headphones are plugged in properly, which I don't recall Gnome doing.

The volume appears to reset after every reboot... but there's a fix:
[http://ubuntuforums.org/showpost.php?p=7621935&postcount=13](http://ubuntuforums.org/showpost.php?p=7621935&postcount=13)

I also installed the 9.04 Aircraft Manager, and added a keyboard shorcut too:
**/usr/bin/aircraft-manager** (Fn+2)

I find the XFCE panel autohide feature more instantaneous than in Gnome (where it slowly slides out), so is better for the precious screen real-estate in the Mini.  However, it does appear to have a bug where the autohiding seems to not work sometimes.

To allow an easy one-click fix whenever this happens, added a launcher with command:
**xfce4-panel -r**

And be creating a top-right panel launcher to close the active window (using gtk-close icon), it is easy to close applications without needing to be too precise:
**xte 'keydown Alt_L' 'keydown F4' 'keyup F4' 'keyup Alt_L' **

Also changed the Theme and Icons to Human, now that I'm accustomed to the look!

This lot are all perfect for the netbook which is used as a proper computer (as mine is).

Another useful tool - catfish for searching:
```
sudo apt-get install catfish
```

And menu editing: [http://bimma.me.uk/2009/04/25/how-to-xfce-46-menu-edit-in-xubuntu-904-jaunty/](http://bimma.me.uk/2009/04/25/how-to-xfce-46-menu-edit-in-xubuntu-904-jaunty/)
Similar to LXDE: [http://ubuntu-lxde.wikidot.com/menu](http://ubuntu-lxde.wikidot.com/menu)
but the file needs to be modified in your users settings (e.g. edit by adding XFCE; to the OnlyShowIn category and copy):
```
cp /usr/share/applications/gnome-network-properties.desktop ~/.local/share/applications/
```

---

