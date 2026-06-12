---
title: "[SOLVED] splash screen on peach background"
date: 2008-03-14
forum: Desktop Effects &amp; Customization
---

### Post by lolzlolz on 2008-03-14
i would like to get rid of the peach wallpaper as my splash screen shows up i would rather have my normal desktop wallpaper showing up behind the splash screen rather than the peach one or at least a different color, is there a way to do this? as it it getting on my nerves that my black splash screen is on top of a peach colored wallpaper then my normal wallpaper loads
aslo my gdm bg color set in gdmsetup or watever is changed but that didint help like it did for other people... :confused:

---

### Post by lolzlolz on 2008-03-16
umm, answer???
sorry for being impatient

(basically bump)

---

### Post by n-alexander on 2008-03-16
> **lolzlolz said:**
> i would like to get rid of the peach wallpaper as my splash screen shows up i would rather have my normal desktop wallpaper showing up behind the splash screen rather than the peach one or at least a different color, is there a way to do this? as it it getting on my nerves that my black splash screen is on top of a peach colored wallpaper then my normal wallpaper loads
aslo my gdm bg color set in gdmsetup or watever is changed but that didint help like it did for other people... :confused:

quote from some other post:

gksudo gedit /etc/gdm/PreSession/Default: on line 61 (right near the end of the file) there's a bit
 that looks like this -

# Default value
if [ "x$BACKCOLOR" = "x" ]; then
BACKCOLOR="#dab082"

i think that is the original value - #dab082 i changed it to a dark colour, to this - BACKCOLOR="#1
C1919"

---

### Post by lolzlolz on 2008-03-21
thx so much

---

