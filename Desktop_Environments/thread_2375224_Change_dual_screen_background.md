---
title: "Change dual screen background"
date: 2017-10-23
forum: Desktop Environments
---

### Post by grezly2 on 2017-10-23
A few days ago i switched from unity 'back'  to Gnome (3.26) while upgrading ubuntu.
I'm working dual screen, and until a few days ago i used a commandshell script that change once everywhile my background image. Both screens showed a different image, i've the following statement for this:
```
feh --bg-scale --no-fehbg --bg-center --bg-max "$file1" "$file2"
```
This piece of code worked perfectly until my upgrade to Gnome. This code doesn't do anything, i already tried to config my background settings but with no succes.

Right now i'm using the following code to change my background image
```
gsettings set org.gnome.desktop.background picture-uri "$file1"
```
Only this piece of code takes 1 argument, and right now i didn't find any solution to change seperatly both the background of my left and right screen.

It is quit a time ago I used Gnome, but does someone knows if i missed something in configuring Gnome, or isn't it possible in Gnome?

---

