---
title: "QT Programs Not Conforming to GTK Themes on Unity"
date: 2014-05-24
forum: Desktop Environments
---

### Post by LillyDragon on 2014-05-24
I have tried several different solutions across the Internet, and I still can't get Skype, VLC, Pidgin, or any other QT dependent app to be consistent with my GTK theme. (I use Numix Bluish, a mod of Numix that supports GTK2, GTK3, Openbox, Unity, Metacity, and XFCE4.) QTConfig4, or even QTConfig3 should have done the trick, but it's not, and I can't understand why.

This may be an issue specific to Unity, as I did not have these problems with XFCE last year. Now that I need a darker theme, and don't want to go back to XFCE, I'm running into problems. Does anyone know what's going on? Am I missing something?

---

### Post by Frogs Hair on 2014-05-24
> This may be an issue specific to Unity, This is an old and on-gong problem that predates Unity and as you have discovered there are numerous work around/s that are successful for some users in some applications.

 I am a pidgin user and have no theme variations on either computer on at least three different releases and didn't know it was a problem  until your post . Bump the post as needed once a day , perhaps someone knows of a work around that you haven't attempted . Please list what you have tried so it is not suggested again.

---

### Post by LillyDragon on 2014-05-25
That's a good thought, Frogs Hair. I'll list what I tried.

I added this line to my .profile file. I also created a similar file named .xinitrc with this line for the heck of it.

```
#apply gtk2.0 theme
export GTK2_RC_FILES="$HOME/.gtkrc-2.0"
```

I have a manually created .gtkrc-2.0 file with this line, correctly stating my theme name.

```
gtk-theme-name="Numix Bluish
include "/usr/share/themes/Numix Bluish/gtk-2.0/gtkrc"
```

I used both the QT 4 Settings app, and its QT 3 counterpart, to set my QT theme to GTK+, instead of "unknown" or "desktop setting". I restarted X by logging out and logging back in, to see if it would take affect. (Which, it didn't.)

Also looked into installing QT themes, so I could at least have a dark theme for QT-based apps, but I can't wrap my head around installing one. I'm beginning to think QT themes are specifically for skinning apps while building them.

I tried putting this into the terminal, in case the theme was not set for GTK2 apps, but this did nothing.

```
gconftool-2 --set --type string /desktop/gnome/interface/gtk_theme "Numix Bluish"
```

Lastly, I tried starting Skype with a specific GTK skin; also accomplished nothing. I tried it with an alternative theme as well, on the offchance it was Numix's fault.

```
GTK2_RC_FILES="/usr/share/themes/Numix Bluish/gtk-2.0/gtkrc" skype
```

So all of this has left me feeling rather frustrated. I simply want a global theme that's easier on my eyes while looking at the screen for long hours, but I can't understand what's making this more complicated than it has to be.

---

### Post by vasa1 on 2014-05-25
> **johnluke728 said:**
> ...
I have a manually created .gtkrc-2.0 file with this line, correctly stating my theme name.

```
gtk-theme-name="Numix Bluish
include "/usr/share/themes/Numix Bluish/gtk-2.0/gtkrc"
```
....
I use
```

include "/home/vasa1/.themes/MyGreybird/gtk-2.0/gtkrc"

gtk-icon-theme-name = "NoInherits"

```
in my .gtkrc-2.0. Also, there should be a " at the end of your first line.

And I don't know if you need to escape the space between Numix and Bluish.

PS: I think you *should* escape every space with \ otherwise bash will think there are two items instead of one!

Ideally, avoid spaces in filenames. Who knows when such things will bite you.

---

### Post by LillyDragon on 2014-05-25
Ouch, I completely missed the lacking quotation mark. Normally, directories wrapped in quotations are okay with spaces in folder names, but I still went ahead and removed the spaces in a local Home copy. Even with this typo corrected, I still get no results after logging back in.

```
gtk-theme-name="NumixBluish"

include "/home/jonathan/.themes/NumixBluish/gtk-2.0/gtkrc"
```

---

### Post by vasa1 on 2014-05-25
> **johnluke728 said:**
> ...

```
#apply gtk2.0 theme
export GTK2_RC_FILES="$HOME/.gtkrc-2.0"
```
Could you temporarily rename that .xinitrc file to something else in case it's interfering?

> **johnluke728 said:**
> 
I have a manually created .gtkrc-2.0 file with this line, correctly stating my theme name.

```
gtk-theme-name="Numix Bluish
include "/usr/share/themes/Numix Bluish/gtk-2.0/gtkrc"
```

I feel the first line isn't needed. Could you comment it out?
> **johnluke728 said:**
> 
...
I tried putting this into the terminal, in case the theme was not set for GTK2 apps, but this did nothing.

```
gconftool-2 --set --type string /desktop/gnome/interface/gtk_theme "Numix Bluish"
```
Can you undo that?
> **johnluke728 said:**
> 
Lastly, I tried starting Skype with a specific GTK skin; also accomplished nothing. I tried it with an alternative theme as well, on the offchance it was Numix's fault.

```
GTK2_RC_FILES="/usr/share/themes/Numix Bluish/gtk-2.0/gtkrc" skype
```
This approach didn't work for me as well in Lubuntu 14.04. I don't know why. Although I stuck **env** at the beginning of that code ([http://askubuntu.com/questions/8336/how-can-one-make-firefox-ignore-my-gtk-theme-entirely](http://askubuntu.com/questions/8336/how-can-one-make-firefox-ignore-my-gtk-theme-entirely)).

---

### Post by vasa1 on 2014-05-25
> **johnluke728 said:**
> Ouch, I completely missed the lacking quotation mark. Normally, directories wrapped in quotations are okay with spaces in folder names, but I still went ahead and removed the spaces in a local Home copy. Even with this typo corrected, I still get no results after logging back in.

```
gtk-theme-name="NumixBluish"

include "/home/jonathan/.themes/NumixBluish/gtk-2.0/gtkrc"
```

Oops! I just read your response more carefully. You're right in that double quotes should protect you. But **Numix Bluish** would become **Numix\ Bluish** and not **NumixBluish**. The \ does the magic.

---

### Post by vasa1 on 2014-05-25
Came across this: [https://wiki.archlinux.org/index.php/Uniform_Look_for_Qt_and_GTK_Applications](https://wiki.archlinux.org/index.php/Uniform_Look_for_Qt_and_GTK_Applications)

---

### Post by LillyDragon on 2014-05-25
I've reviewed that page as well, but a lot of those are for KDE users, and KDE's system settings manager doesn't play nice with Unity, according to reviews. KDE sure is sounding more appealing, however. I only had it once while trying out PCLinux2007, and I quite liked it, although customization felt a little challenging, so I stuck to Gnome2 on Ubuntu back then.

And I'll try uncommenting the theme name. I've also gotten rid of the .xinitrc file, since Ubuntu Unity pays attention to the .profile anyway. I don't think it even acknowledged the presence of .xinitrc.

---

### Post by vasa1 on 2014-05-26
> **johnluke728 said:**
> ... and I still can't get Skype, VLC, Pidgin, or any other QT dependent app to be consistent with my GTK theme. ...
When you say consistent, just how differently do those apps look? Maybe a screenshot showing a few qt apps that aren't looking good with a gtk app that looks the way you want. I mean are there minor differences or huge ones?

---

### Post by vasa1 on 2014-05-28
> **vasa1 said:**
> ...
This approach didn't work for me as well in Lubuntu 14.04. I don't know why. Although I stuck **env** at the beginning of that code ([http://askubuntu.com/questions/8336/how-can-one-make-firefox-ignore-my-gtk-theme-entirely](http://askubuntu.com/questions/8336/how-can-one-make-firefox-ignore-my-gtk-theme-entirely)).
It works. Maybe there was a coffee-insufficiency condition.

Examples:
```
env GTK2_RC_FILES=/usr/share/themes/Lubuntu-default/gtk-2.0/gtkrc leafpad
env GTK2_RC_FILES=/usr/share/themes/Lubuntu-default/gtk-2.0/gtkrc libreoffice --calc
```

---

### Post by LillyDragon on 2014-05-30
Okay, so it turns out Numix Bluish had a dead useless GTKRC file for GTK2 theming, so everything was going to default Ambiance. (Thankfully, I wasn't experiencing QT theming problems.)

So I copied the GTK2 dark variant of Ambiance into the GTK2 folder inside the NumixBluish theme, and now I've got Skype nice and dark! Pidgin, Firefox, VLC, everything's using it now!

I feel bad for blaming my issue on other things now. It takes me forever to figure out what's wrong with something because of this. :P Thanks for helping me wrap up every possibility with QT/GTK, vasa1!

---

### Post by vasa1 on 2014-05-30
> **johnluke728 said:**
> ... Thanks for helping me wrap up every possibility with QT/GTK, vasa1!
You're welcome. I've used the Numix theme that comes as part of shimmer-themes (free when you install Xubuntu or the xfce desktop) and that's pretty complete. If I don't like a particular color, I just edit the relevant file and put in the color I like.

---

