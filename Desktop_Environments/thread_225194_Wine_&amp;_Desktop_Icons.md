---
title: "Wine &amp; Desktop Icons"
date: 2006-07-29
forum: Desktop Environments
---

### Post by darden68 on 2006-07-29
Hi,

On a previous installation of Dapper, when installing software within Wine, I automatically had the correct icon/link on my desktop, like I would have had  with Windows.
Now that I have reinstalled Dapper from scratch, installing software with Wine only create a .lnk file with no icon on my desktop.

Did I miss something in the wine configuration ?
Wine is installed from the WineHQ rep.

Thanks in advance !

---

### Post by ESPOiG on 2006-07-29
just make ur own link to the program, eg like set it so u have the windows .ico as the pic or use gimpy to convert to png/xpm and then make the linux link to the program, like so

wine ~/.wine/c_drive/Program Files/Crap/Crap.exe

i thinks that is right :P... give it a try if it dont work ill get bak to u :D

---

### Post by darden68 on 2006-07-29
thanks ESPOiG, i'll use that as a workaround.
Now some programs don't have the .ico, i think the icon is included in the .exe...
i could always find a way to extract this icon from the .exe (i've seen that somewhere in the forum), but still, as it was done automatically before with default settings, i wonder what has changed so now i have to do it manually... maybe an intermediate version of Wine had this feature and it's no more in the latest version.

if anyone has seen the same thing happened on his machine, i would be interested to know how to fix it :)

---

### Post by ESPOiG on 2006-08-01
there is lots of programs for extracting icons from exe's but i doubt they would run properly under wine, try booting into windows, and finding ur program and dl the program called resource hacker or res hacker, and edit the .exe and extract the icon from the icon group :D... then transfer to linux, by mountin windows partitions or using usb drive etc

---

### Post by sawjew on 2006-08-01
If you just go to ~/.gnome/apps/Wine/Programs you will find launchers for most of your wine programs here, just drag them onto your desktop.  If you want to create your own launcher and need to extract an icon, use icon sucker ([http://www.iconsucker.com]("http://www.iconsucker.com")), it works perfectly under wine and Ubuntu can use the standard .ico format.

---

### Post by darden68 on 2006-08-04
> try booting into windows, and finding ur program

I have nothing left of any Windows partition :)

>  If you just go to ~/.gnome/apps/Wine/Programs you will find launchers for most of your wine programs here

Thanks a lot ! That was exactly what i was looking for ! i won't know why they used to automatically show up on the desktop, but i'm happy to move them manually :)

---

### Post by theToolman on 2006-12-16
> **sawjew said:**
>  If you want to create your own launcher and need to extract an icon, use icon sucker ([http://www.iconsucker.com]("http://www.iconsucker.com")), it works perfectly under wine and Ubuntu can use the standard .ico format.

This installed neatly and quickly in wine, easily got output (ico or bmp), but had to convert png for Ubuntu icon support.  On the command line in the folder where the images are:

```
for i in *.ico; do convert "$i" "$i.png"; done
```
or
```
for i in *.bmp; do convert "$i" "$i.png"; done
```

---

### Post by sawjew on 2006-12-19
For anyone who wants to extract icons from windows executables I initially recommended Iconsucker but I have since found an application which will do the same thing, but save the icons as png's straight away, thus eliminating the need for conversion.

The application is called Wineicons and is available here [http://wineicons.sourceforge.net/]("http://wineicons.sourceforge.net/")

---

### Post by B00R4dL3y on 2007-02-19
Is it okay to delete the .lnk icons/files on the desktop or are they needed?

---

