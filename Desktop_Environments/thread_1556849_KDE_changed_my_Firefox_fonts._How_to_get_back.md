---
title: "KDE changed my Firefox fonts. How to get back?"
date: 2010-08-20
forum: Desktop Environments
---

### Post by Roasted on 2010-08-20
I installed KDE on my Ubuntu laptop and then got rid of it. I used puregnome which worked but I still have weird fonts in Firefox. I tried adjusting the preferences in Firefox but nothing works. How can I revert it back?

LOL. I did a fresh install (but kept my home directory) and it made no change. I also removed the .mozilla folder entirely and uninstalled/reinstalled Firefox. No change.

How can I get this back? I'm a little annoyed at the way Firefox looks now with these KDE fonts. :(

---

### Post by lovinglinux on 2010-08-20
I'm not sure if it will work, but try to rename the file ~/.gtkrc-2.0 to something else or delete it.

---

### Post by Roasted on 2010-08-21
Deleted it. No change.

I need my fonts back. This KDE font sucks. :(

---

### Post by Ms_Angel_D on 2010-08-21
I never understood why kde mixed with gnome messed up the fonts so bad, because when you install straight kubuntu they look much nicer same as when you install just ubuntu with only gnome. Something about the mix is just bad.

try removing ~/.fonts.conf then rebooting and see if that makes a difference.

---

### Post by Zorael on 2010-08-21
To get KDE to display GTK apps well, you really need the **~/.gtkrc-2.0-kde4** theming that **kubuntu-default-settings** adds. Installing this will likely change your bootup logo to Kubuntu's though, so expect that. (You will obviously need **kcm-gtk** as well.)

You get all those packages when you install **Kubuntu**, but if you're just trying to install minimum-level KDE packages you'll have to fix it yourself.

Whenever you change font settings in KDE, it first saves the changes in the normal KDE settings file **~/.kde/share/config/kdeglobals** that all KDE and KDE settings-aware programs read, and then also saves basic font settings (autoaliasing, hinting etc) in **~/.fonts.conf**, for apps that don't have good KDE integration. What I guess is happening here is that the **.fonts.conf** settings transfer to your GNOME session. So, delete or rename it.

```
$ mv ~/.fonts.conf ~/.fonts.conf.bak
```

---

### Post by Roasted on 2010-08-21
> **Zorael said:**
> To get KDE to display GTK apps well, you really need the **~/.gtkrc-2.0-kde4** theming that **kubuntu-default-settings** adds. Installing this will likely change your bootup logo to Kubuntu's though, so expect that. (You will obviously need **kcm-gtk** as well.)

You get all those packages when you install **Kubuntu**, but if you're just trying to install minimum-level KDE packages you'll have to fix it yourself.

Whenever you change font settings in KDE, it first saves the changes in the normal KDE settings file **~/.kde/share/config/kdeglobals** that all KDE and KDE settings-aware programs read, and then also saves basic font settings (autoaliasing, hinting etc) in **~/.font.conf**, for apps that don't have good KDE integration. What I guess is happening here is that the **.fonts.conf** settings transfer to your GNOME session. So, delete or rename it.

```
$ mv ~/.fonts.conf ~/.fonts.conf.bak
```

Bam! Winner! Thanks for the help guys.

---

### Post by sineau on 2011-05-27
> **Zorael said:**
> To get KDE to display GTK apps well, you really need the **~/.gtkrc-2.0-kde4** theming that **kubuntu-default-settings** adds. Installing this will likely change your bootup logo to Kubuntu's though, so expect that. (You will obviously need **kcm-gtk** as well.)

You get all those packages when you install **Kubuntu**, but if you're just trying to install minimum-level KDE packages you'll have to fix it yourself.

Whenever you change font settings in KDE, it first saves the changes in the normal KDE settings file **~/.kde/share/config/kdeglobals** that all KDE and KDE settings-aware programs read, and then also saves basic font settings (autoaliasing, hinting etc) in **~/.fonts.conf**, for apps that don't have good KDE integration. What I guess is happening here is that the **.fonts.conf** settings transfer to your GNOME session. So, delete or rename it.

```
$ mv ~/.fonts.conf ~/.fonts.conf.bak
```

Just wanna say thank you. I teared google out and found nothing. Just renamed ~/.kde and ~/.fonts.conf and now everything's ok (I don't need KDE anyways, it looks like a spaceship)

---

### Post by blauendonau on 2011-05-27
I found this solution to be very useful as well, thank you. A lot of people are running dual DEs nowadays after being disappointed with Unity, so maybe this could be added to a Firefox sticky somewhere?

---

### Post by OM NOM NOM on 2011-09-07
Many thanks for this. Was absolutely tearing my hair out trying to figure out a way to reset the fonts. MUCH better :-)

---

### Post by gippeswyc on 2011-10-24
what he said :)

---

### Post by Roasted on 2011-10-24
Wow - good to see other users are finding it useful. I had completely forgotten I even posted this.

Marked as solved. :guitar:

---

### Post by Fende on 2012-06-28
> **Zorael said:**
> To get KDE to display GTK apps well, you really need the **~/.gtkrc-2.0-kde4** theming that **kubuntu-default-settings** adds. Installing this will likely change your bootup logo to Kubuntu's though, so expect that. (You will obviously need **kcm-gtk** as well.)

You get all those packages when you install **Kubuntu**, but if you're just trying to install minimum-level KDE packages you'll have to fix it yourself.

Whenever you change font settings in KDE, it first saves the changes in the normal KDE settings file **~/.kde/share/config/kdeglobals** that all KDE and KDE settings-aware programs read, and then also saves basic font settings (autoaliasing, hinting etc) in **~/.fonts.conf**, for apps that don't have good KDE integration. What I guess is happening here is that the **.fonts.conf** settings transfer to your GNOME session. So, delete or rename it.



```
$ mv ~/.fonts.conf ~/.fonts.conf.bak
```


This solution has worked for me with version 12.04. Thank you very much.

---

