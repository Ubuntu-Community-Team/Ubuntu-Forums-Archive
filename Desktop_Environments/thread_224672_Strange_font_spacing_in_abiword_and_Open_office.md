---
title: "Strange font spacing in abiword and Open office"
date: 2006-07-28
forum: Desktop Environments
---

### Post by Biffy on 2006-07-28
This is hard to explain so i'll post a picture:

[http://img142.imageshack.us/my.php?image=gkrellshoot072806172731sn6.jpg](http://img142.imageshack.us/my.php?image=gkrellshoot072806172731sn6.jpg)

Notice that spacing between the "a" and "f" ? I have this problem on my system, and first i tought it was a problem with abiword, but it's also there in OO and leafpad.

I am suspecting a DPI setting. I am not using GDM, i boot right into the console and i start X with the command "startx" . Can i somehow see wich DPI setting i have? How can i change it? This happens with the "times new roman" font, but it also happens with others.

If there's another fix for this, i appreciate it.

---

### Post by Biffy on 2006-07-28
Found this is my xorg.conf :

```
Section "Files"
			# local font server
	# if the local font server has problems, we can fall back on these
        # paths to defoma fonts
	FontPath     "unix/:7100"
	FontPath     "/usr/lib/X11/fonts/misc"
	FontPath     "/usr/lib/X11/fonts/cyrillic"
	FontPath     "/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/lib/X11/fonts/Type1"
	FontPath     "/usr/lib/X11/fonts/CID"
	FontPath     "/usr/lib/X11/fonts/100dpi"
	FontPath     "/usr/lib/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection
```

Also, if i write a document in Abiword and then open it at work (using windows machines) it all look normal. So, everything i writes looks funny on my screen but not on others.

---

### Post by Biffy on 2006-07-28
Update:

```
larsson@ubuntu:/usr/bin $ xdpyinfo| grep resolution
  resolution:    100x100 dots per inch
```

100x100 DPI . Is that normal? May that be causing my problems?

---

