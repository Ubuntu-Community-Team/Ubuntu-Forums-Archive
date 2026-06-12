---
title: "how to enable xfce panel transparency ?"
date: 2005-04-30
forum: Desktop Environments
---

### Post by suoko on 2005-04-30
Hi,

I'm running hoary with latest xfce packages and I was wondering how to enable transparency of bottom panel.
I tried adding to xorg.conf :
Section "Extensions"
  Option "Composite" "Enable"
  Option "RENDER" "Enabled"
  Option "DAMAGE" "Enabled"
EndSection

and 

Option          "RenderAccel"           "true"

[for my nvidia card]

Then I installed libxcomposite1, xcompmgr as well as transset.
I created the .config/xfce/transparency file adding:
panel=40
.....

BUT NOTHING CHANGES !!!    ](*,) 


Any idea on how to enable the panel transparency ?

---

### Post by Juippisi on 2005-04-30
Well, I did it using transset (click the panel). I Don't really know how not to make icons transparent. Here is a little screenshot
[http://www.roskakori.org/juippis/pictures/screenshots/xfce4-panel_transparent.jpg](http://www.roskakori.org/juippis/pictures/screenshots/xfce4-panel_transparent.jpg)

I personally don't use XFce, I like fluxbox :).

---

### Post by rosslaird on 2005-05-01
You can make the xfce panel transparent using transset, but xfce comes with its own composite/transparency manager which defaults to a small amount of panel transparency (i.e. my panel is somewhat transparent until my cursor moves onto it; then it becomes solid). You cannot make the icons remain solid and change the transparency of the panel itself. Such features will be in the next xfce release (as I understand it).

Ross

---

### Post by Psquared on 2005-05-05
[QUOTE=rosslaird]You can make the xfce panel transparent using transset, but xfce comes with its own composite/transparency manager which defaults to a small amount of panel transparency (i.e. my panel is somewhat transparent until my cursor moves onto it; then it becomes solid). You cannot make the icons remain solid and change the transparency of the panel itself. Such features will be in the next xfce release (as I understand it).

Ross[/QUOTE]

I can't figure out how to do this. Where is the setting?

---

### Post by rosslaird on 2005-05-05
It's been a while since I've used xcompmgr and transset (as they are so unstable), but as I recall:

1. open a console
2. type transset
3. The cursor will change (to a cross).
4. click on the panel (or whatever you want to "transparentize")

This should make the panel go to the default transparency (I think it's 20 per cent).

Ross

---

### Post by dickohead on 2005-09-20
[QUOTE=rosslaird]It's been a while since I've used xcompmgr and transset (as they are so unstable), but as I recall:

1. open a console
2. type transset
3. The cursor will change (to a cross).
4. click on the panel (or whatever you want to "transparentize")

This should make the panel go to the default transparency (I think it's 20 per cent).

Ross[/QUOTE]
 and how does one make sure that these items stay transparent after you log in and out? I have xcompmgr loading when xfce startsup, but i am unable to get the items i have transseted to stay that way, any help would be great!!!

---

