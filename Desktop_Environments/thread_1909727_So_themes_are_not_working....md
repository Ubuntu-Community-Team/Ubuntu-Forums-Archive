---
title: "So themes are not working..."
date: 2012-01-15
forum: Desktop Environments
---

### Post by pitroadrush on 2012-01-15
Hello, Ubuntu 11.10 
Has anyone having or have problems adding themes to Ubuntu 11.10 ? 
I have done:
1- I download it or saved either way
2- extracted to .theme in the home folder
3- I'll go to advance settings/theme to change it, guess what, no show
and
on the bottom, shell theme and a yellow -->[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG]<-- admiration is on the conner.  :confused:
I cant see any new themes.
Suggestions please. 

Mk

---

### Post by freebird54 on 2012-01-15
No expert here - but I have some theme changes going here.  One possible source of troubles is themes need to be GTK3 rather than GTK2 based.

Running with changes to Icons (Faenza - Radiance),GTK+ Theme (Adwaita Cupertino SL Unity) and Window (My-Metal) - if that helps you at all

Good luck

---

### Post by bluexrider on 2012-01-16
I thought system themes were in the /usr/share/themes folder ???

Might ```
cat /usr/share/themes/*
```
Just to see....

---

### Post by freebird54 on 2012-01-16
There are themes there, but apparently it is not necessary to locate them there (and you need to sudo to get them there).  I have a .themes directory in $HOME, and that is where I installed the ones I downloaded, and chose from using the "Advanced Settings".

Hope that helps...

---

### Post by mcduck on 2012-01-16
> **pitroadrush said:**
> Hello, Ubuntu 11.10 
Has anyone having or have problems adding themes to Ubuntu 11.10 ? 
I have done:
1- I download it or saved either way
2- extracted to .theme in the home folder
3- I'll go to advance settings/theme to change it, guess what, no show
and
on the bottom, shell theme and a yellow -->[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG]<-- admiration is on the conner.  :confused:
I cant see any new themes.
Suggestions please. 

Mk
First, make sure the theme you downloaded is a GTK3 theme.

(GTK2 theme alone will not work, but if the GTK3 theme also has GTK2 support included that would definitely be a good idea).

Second, keep in mind that Gnome Shell themes only apply to Gnome Shell, not to Unity or any other desktop session. And you need to have the User Themes extension for the Shell installed.

---

### Post by freebird54 on 2012-01-16
I just spotted something else that might help (it looks like the kind of thing I missed when I first started trying th change things).  There is a typo in your description of what you have tried - the folder should be named **.themes** not .theme

If the same typo happened when you created it... :)

Just a thought

---

### Post by pitroadrush on 2012-01-16
> **freebird54 said:**
> I just spotted something else that might help (it looks like the kind of thing I missed when I first started trying th change things).  There is a typo in your description of what you have tried - the folder should be named **.themes** not .theme

If the same typo happened when you created it... :)

Just a thought

Cool is working, now I just need to get more compatible, seems I have a few I cant load, which I believe their "maybe" old version of themes.

---

### Post by saneearth on 2012-01-16
I have better luck with the advanced settings manager which I downloaded from synaptic. I get more options and if I have downloaded the proper themes they show up and I can make changes. Still trying to re-find my way around gnome3 and Unity.

---

