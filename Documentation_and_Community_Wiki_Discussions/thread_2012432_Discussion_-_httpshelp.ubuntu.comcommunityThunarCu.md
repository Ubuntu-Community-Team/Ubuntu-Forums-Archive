---
title: "Discussion - https://help.ubuntu.com/community/ThunarCustomActions"
date: 2012-06-29
forum: Documentation and Community Wiki Discussions
---

### Post by Elfy on 2012-06-29
Please use this thread for discussion regarding

[https://help.ubuntu.com/community/ThunarCustomActions](https://help.ubuntu.com/community/ThunarCustomActions)

Support threads should be posted in normal forums.

Thank you.

---

### Post by scania_gti on 2012-08-19
Convert animated gif from selected images:
```
convert -loop 0 -dispose 2 %F %F.gif
```
command "convert" is a part of imagemagick, and more customisation  you will find [http://www.imagemagick.org/script/command-line-tools.php](http://www.imagemagick.org/script/command-line-tools.php)
This custom action need a polishing - don't now how - sometimes imagemagick croping images.
Edited: ```
convert -loop 0 -dispose 2 -layers OptimizeTransparency %F %F.gif
``` this custom command make smaller gif's
Resolution of animated gif is taken from first image in selection. If first have 100x200 pixels - animation will get same resolution.
This command great for my, cause pencil (program to create animations) not exporting to any file :D
And my kids like to draw animations for theirs phones :)

---

### Post by Merrattic on 2012-09-02
A nice simple one

Nano as Root

```
xfce4-terminal -e "sudo nano %f"
```you could add your password to cut out having to type it (not secure):

```
xfce4-terminal -e "echo "yourpasswd" | sudo -S nano %f"
```

---

### Post by Digger109 on 2013-04-03
Here is a Thunar custom action that will send a file's basename, stripped of its file identifier, to xclip.  It works for filenames with extra periods in them, as well as for filenames with spaces in them:


```
qtnhygghj=%n ; echo -n "${qtnhygghj%%.*}" | xclip -selection c

```

IHTH someone!

---

### Post by berteh on 2016-01-28
Hello.

3 actions to manage samba share from thunar right-click on folder are documented below:
[http://ubuntuforums.org/showthread.php?t=2311605](http://ubuntuforums.org/showthread.php?t=2311605)

Could you please add them to the doc page? I don't have right access to do it. thanks.

---

### Post by Digger109 on 2016-08-04
Here is a Thunar custom action that will display a zenity window containing an image's Exif data that is contained in the "Exif comment" line of said data:

```
exiv2 %f  2>&1 | grep -e "Exif comment" | zenity --width=800 --height=240 --text-info --title "%n Exif Comment Data"
```

IHTH someone!

---

### Post by enricobe on 2016-10-31
Hi, 
on my Xubuntu 16.04 the "terminal -e" actions doesn't work. The one which works is "xfce4-terminal -e". Maybe the page needs to be updated with 'xfce4-terminal' instead of 'terminal'?

---

