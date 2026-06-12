---
title: "Newbie help, need more icons"
date: 2006-05-13
forum: Desktop Environments
---

### Post by edotistic on 2006-05-13
I'm extremely new to Linux, so the last couple of days have been living hell - but I stuck with it and have been able to install most of the programs (codecs and so on) that I was using under Windows...and everything seems to be running quite ok.

I'm now ready to "Pimp My Desktop" (if you will). I've been installing some Icon Sets and fiddliing with some themes, no problem there.
Problem is, I would like to change some of the app icons and change the icons on some of the shortcuts I've made on the panels.

I've figured out, that I can right-click on the existing icons and change them under "properties" - but most of the options are not...well...that cool (and most of those icons are already used by other programs).

If I wanted to change the, say, black XMMS icon into something a bit more fancy pantsy - how would I do that??
I downloaded some free icons (.png) and tried to browse to their folder (after right-clicking on the icon I wanted to change), but without any luck.

In Windows I just kept a folder with tons of different icons, right-clicked on stuff I wanted to change and picked something fitting out of that folder - this is what I would like to do.

Any help would be much appreciated, cheers!

---

### Post by louis_nichols on 2006-05-13
It works pretty the same in ubuntu. As icon for a launcher, you can choose pretty much any png image from your hard-disk... You're saying you haven't had much luck with that. What exactly happened?

---

### Post by brettr on 2006-05-13
Hey, I am fairly new as well and  have been playing around with this as well... i know that a lot of the icons are stored in /usr/share/pixmaps ... so basically what i did was just open up Gimp and save the icon as a .xpm and then copied it to /usr/share/pixmaps.

Although i am sure there is a better and proper way to do this heh...

---

### Post by edotistic on 2006-05-13
I downloaded a set of icons with a lot of .png's in several different folders (16x16, 32x32 - by size). When I go and browsed for them, they are "greyed out" and un-clickable once I get to them.

They're all in .png, not .xmp as some of the other icons in the /pixmaps folder. However, a lot of the icons are .png in the /pixmaps folder.

I don't understand it...

---

### Post by louis_nichols on 2006-05-13
Well... when the small screen with icons comes up, you will have a browse button there... unless you are talking about a different configuration screen.

Are you trying to configure launchers on desktop, or menu entries via alacarte, or panel shortcuts?

Copying png's to pixmaps folder is indeed a possible solution. Other icons are under /usr/share/icons...

---

### Post by brettr on 2006-05-13
Hmm... Strange... if you use the browse function it will gray out the files, however if you type the directory manually it will show all the pictures... jpg, png... etc

---

### Post by louis_nichols on 2006-05-13
[QUOTE=edotistic]I downloaded a set of icons with a lot of .png's in several different folders (16x16, 32x32 - by size). When I go and browsed for them, they are "greyed out" and un-clickable once I get to them.

They're all in .png, not .xmp as some of the other icons in the /pixmaps folder. However, a lot of the icons are .png in the /pixmaps folder.

I don't understand it...[/QUOTE]

I presume you're talking about alacarte. I encounter the same problem and I don't get it wither.

But a workaround is this: decide on which icon you'd like to have for a certain app. Te entries in the Applications menu are stored under /home/<user name>/.local/share/applications as text files with extension .desktop. So choose the one you want to edit, open it with a text editor and you will see something like:

```
[Desktop Entry]
Name=DC++
Exec=/home/myself/downloads/^src/__dc_stuff/linuxdcpp/ldcpp
Encoding=UTF-8
Terminal=false
Type=Application
Name[en_US]=DC++
Icon=/usr/share/pixmaps/avantgo.png
```

So just change the path to the icon you want after "Icon="

EDIT: same answer to brettr's problem.

---

### Post by edotistic on 2006-05-13
[QUOTE=louis_nichols]Well... when the small screen with icons comes up, you will have a browse button there... [/QUOTE]

yup, that's the one. 

I'm right-clicking on the XMMS icon (that I put in one of the panels), and also some shortcuts to folders on my hdd.

That small screen, with all the icons ("/pixmaps") has a limited amount of icons (most of them are app icons, already in use; Firefox, Gaim). If I instead use the "browse" option, and navigate to the folder with all the icons I downloaded - I can't choose any of them, they're greyed out.

Oh yeah, I don't seem to have any /shared/icons/ folder. There are a lot of icons in /shared/, thou. Lemme see if I can figure out how to get a screenshot of it.

[Screenshot.png]("http://edotistic.com/aintro/Screenshot.png")

---

