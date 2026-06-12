---
title: "User selected Desktop Wallpaper becomes Login Wallpaper as well."
date: 2013-05-16
forum: Desktop Environments
---

### Post by Teknor on 2013-05-16
Once I upgraded from Xubuntu 12.10 to 13.04, everytime I change my Desktop Wallpaper Image, that image becomes the wallpaper shown on the login screen as well as my desktop wallpaper.

I've checked (and re-edited) the /etc/lightdm/lightdm-gtk-greeter.conf to make sure it is pointing to the correct wallpaper file ("background=/lib/plymouth/themes/xubuntu-logo/xubuntu-greybird.png") and that the xubuntu-greybird.png file is in the correct place (it is, has never been moved since original installation).

Any ideas?  Suggections?

---

### Post by marianoa on 2013-05-16
@Teknor: what is the content of /etc/lightdm/lightdm-gtk-greeter.conf and /etc/lightdm/lightdm.conf in your install?

---

### Post by Dennis N on 2013-05-16
> **Teknor said:**
> Once I upgraded from Xubuntu 12.10 to 13.04, everytime I change my Desktop Wallpaper Image, that image becomes the wallpaper shown on the login screen as well as my desktop wallpaper.

I've checked (and re-edited) the /etc/lightdm/lightdm-gtk-greeter.conf to make sure it is pointing to the correct wallpaper file ("background=/lib/plymouth/themes/xubuntu-logo/xubuntu-greybird.png") and that the xubuntu-greybird.png file is in the correct place (it is, has never been moved since original installation).

Any ideas?  Suggections?

I can confirm this behavior with Xubuntu 13.04. Must be a new feature. This happens even if you select a desktop background stored in you home folder, so how this works out with multiple users as to what the greeter screen presents during login is another question.

The 'background= ' line in the lightdm-gtk-greeter.conf file no longer seems to be used to control the wallpaper, and it does not change when you change the desktop background through the desktop settings.

---

### Post by brainwash on 2013-05-16
AccountsService sets the users background (/var/lib/AccountsService/users/<user>).

---

### Post by Dennis N on 2013-05-16
Thanks for the reply. 

I see that the file in account services that you point out stores the path to the user's desktop background (the background chosen in the "Desktop Settings" dialog), but the issue is that the lightdm greeter in Xubuntu 13.04 is always using this **same** background with no obvious way to make different choices for desktop and the lightdm greeter. 

Before this 13.04 release, the greeter background was defined in the lightdm-gtk-greeter.conf file (see post #1) independent of the desktop. This setting now seems to be is ignored, and the greeter mimics the desktop background instead - when you change the desktop background, the greeter background changes too.

What we are looking for is how can the administrative user set the lightdm-gtk-greeter background in Xubuntu 13.04 independent of the desktop background?

---

### Post by marianoa on 2013-05-17
@Dennis N: what is the content of /etc/lightdm/lightdm-gtk-greeter.conf and /etc/lightdm/lightdm.conf in your install?

---

### Post by Dennis N on 2013-05-17
> **marianoa said:**
> @Dennis N: what is the content of /etc/lightdm/lightdm-gtk-greeter.conf and /etc/lightdm/lightdm.conf in your install?

Sure. 

/etc/lightdm/lightdm-gtk-greeter.conf is a symbolic link, and the ultimate target is at:

dn@Kayleigh:/etc/xdg/xdg-xubuntu/lightdm$ cat lightdm-gtk-greeter.conf 

```

#
# background = Background file to use, either an image path or a color (e.g. #772953)
# theme-name = GTK+ theme to use
# icon-theme-name = Icon theme to use
# font-name = Font to use
# xft-antialias = Whether to antialias Xft fonts (true or false)
# xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
# xft-hintstyle = What degree of hinting to use (hintnone, hintslight, hintmedium, or hintfull)
# xft-rgba = Type of subpixel antialiasing (none, rgb, bgr, vrgb or vbgr)
# show-language-selector (true or false)
# show-indicators = semi-colon ";" separated list of allowed indicator modules (e.g. indicator-sound.so)
#
[greeter]
background=/lib/plymouth/themes/xubuntu-logo/xubuntu-greybird.png
theme-name=Greybird
icon-theme-name=elementary-xfce
font-name=Droid Sans 10
xft-antialias=true
xft-dpi=96
xft-hintstyle=slight
xft-rgba=rgb
show-language-selector=true
show-indicators=

```

**lightdm.conf:**

dn@Kayleigh:/etc/lightdm$ cat lightdm.conf

```
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=xubuntu

```

Will test the solid color option for 'background= ' in a moment and see if I get any signs of life.

---

### Post by Dennis N on 2013-05-17
> **Dennis N said:**
> Will test the solid color option for 'background= ' in a moment and see if I get any signs of life.

Entered a solid color for the background in lightdm-gtk-greeter.conf:

```
[greeter]
#background=/lib/plymouth/themes/xubuntu-logo/xubuntu-greybird.png
background=#74cc9a
theme-name=Greybird
icon-theme-name=elementary-xfce
font-name=Droid Sans 10
xft-antialias=true
xft-dpi=96
xft-hintstyle=slight
xft-rgba=rgb
show-language-selector=true
show-indicators=

```

I conclude the line 'background= ' is not ignored, since initially the solid background appears for a fraction of a second, then is set immediately to the desktop background. So that ultimate setting is being made elsewhere. 

I'm not testing this since it does not apply to me, but if there are multiple users each with a different background choice, the question arises as to which gets displayed in the greeter, since the background appears before login? Also the background can be located in a user's home folder. 

In my case, I prefer the backgrounds to be the same, but some users (as the O.P.) don't.

---

### Post by marianoa on 2013-05-17
I think that here there's something interesting for your case
[http://askubuntu.com/questions/64001/how-do-i-change-the-wallpaper-in-lightdm/121594#121594](http://askubuntu.com/questions/64001/how-do-i-change-the-wallpaper-in-lightdm/121594#121594)

The equivalent gui procedure should be via dconf-editor. I'm on Ubuntu and if I open dconf-editor and search for unity-greeter I can find the settings related to it, one of them reads "draw-user-backgrounds", it is enabled and I get the behaviour you want to get rid of. In dconf-editor you should search for lightdm-gtk-greeter and disable the "draw-user-backgrounds" option

---

### Post by Dennis N on 2013-05-17
@marianoa

Thanks for the link and ideas. I will look into those. I hope the O.P. finds something there as well to solve his problem.

---

### Post by Dennis N on 2013-05-17
Had some time to check dconf settings with the dconf-editor (as suggested by marianoa) to see what it had to offer. There are no entries for lightdm-gtk-greeter, and a search with it's 'find' option for either 'greeter' or 'lightdm' returns nothing.

I will stick with the current setup. I prefer the backgrounds being the same.
 
Sorry, no solution or help to offer to anyone wanting different backgounds.

---

### Post by marianoa on 2013-05-17
I have to admit that I tried the dconf-editor method and it didn't work for me either but the method described in the link I posted before works
[http://askubuntu.com/questions/64001/how-do-i-change-the-wallpaper-in-lightdm/121594#121594](http://askubuntu.com/questions/64001/how-do-i-change-the-wallpaper-in-lightdm/121594#121594)

I'm on ubuntu though, for xubuntu it should be modified somehow

---

### Post by Dennis N on 2013-05-18
> **marianoa said:**
> I have to admit that I tried the dconf-editor method and it didn't work for me either but the method described in the link I posted before works
[http://askubuntu.com/questions/64001/how-do-i-change-the-wallpaper-in-lightdm/121594#121594](http://askubuntu.com/questions/64001/how-do-i-change-the-wallpaper-in-lightdm/121594#121594)

I'm on ubuntu though, for xubuntu it should be modified somehow

The method in the link (top answer) works for Ubuntu and unity-greeter, but won't for Xubuntu and lightdm-gtk-greeter - reason: in Xubuntu, there is no schema (group of settings) available to work with.
 
**From Ubuntu 12.04:**

```
dn@Roxanne:~$ gsettings list-schemas | grep greeter
[COLOR="#FF0000"]com.canonical.unity-greeter
[/COLOR]
```
we get the relevant schema to modify with gsettings.

**But, From Xubuntu 13.04:**

```
dn@Roxanne:~$ gsettings list-schemas | grep greeter
dn@Roxanne:~$ 

```
comes up with nil.

---

### Post by freedmax on 2013-10-04
[http://askubuntu.com/questions/140910/unity-greeter-background-not-changing-for-users-automatically-after-upgrade](http://askubuntu.com/questions/140910/unity-greeter-background-not-changing-for-users-automatically-after-upgrade)

"Enable the background plugin from the **accounts daemon**. Run the command gsettings set org.gnome.settings-daemon.plugins.background active true. (This will have the accounts-daemon process update the /var/lib/AccountsService/users/johndoe file with John Doe's wallpaper location.)"

So to disable background plugin from the accounts deamon, run the command 
gsettings set org.gnome.settings-daemon.plugins.background active false 
(or use dconf-tools).
This works with both lightdm-gtk-greeter that with unity-greeter.

If this still does not work, edit as root the file
/usr/share/dbus-1/system-services/org.freedesktop.Accounts.service 
and change the line
Exec=/usr/lib/accountsservice/accounts-daemon
to
#Exec=/usr/lib/accountsservice/accounts-daemon
and reboot.

---

### Post by Buntu Bunny on 2013-10-05
Interesting thread. I have this happening in Ubuntu 12.04 as well; two users, one with Gnome Classic DE and one with Xfce DE. The wallpaper/login background switches occur for both DE's but aren't consistent.

---

