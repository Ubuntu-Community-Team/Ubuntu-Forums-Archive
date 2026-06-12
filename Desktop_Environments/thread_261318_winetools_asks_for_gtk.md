---
title: "winetools asks for gtk"
date: 2006-09-20
forum: Desktop Environments
---

### Post by mello151 on 2006-09-20
I just followed the wine tutorial to install wine and winetools located here:
[http://www.ubuntuforums.org/showthread.php?t=149585&highlight=kubuntu+wine](http://www.ubuntuforums.org/showthread.php?t=149585&highlight=kubuntu+wine)

I made to where I first use winetools with "wt" but I get this error message when I try to use it:
```

mel@tux:/root$ wt
detecting Wine version... done.
Drive C: is /home/mel/.wine/drive_c
Wine 0.9.9
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
WINEVER is "0.9.9".
/usr/local/winetools/Xdialog: Error initializing the GUI...
Do you run under X11 with GTK+ v1.2.0+ installed ?
Calls to wine are executed as  "wine".
Config is /home/mel/.wine/winetools.log.
/usr/local/winetools/Xdialog: Error initializing the GUI...
Do you run under X11 with GTK+ v1.2.0+ installed ?
/usr/local/winetools/Xdialog: Error initializing the GUI...
Do you run under X11 with GTK+ v1.2.0+ installed ?
/usr/local/winetools/Xdialog: Error initializing the GUI...
Do you run under X11 with GTK+ v1.2.0+ installed ?

```

Has anyone else seen this or better yet, know how I can fix it?

---

### Post by funkydan2 on 2006-09-20
I don't think you need winetools with the version of Wine in Dapper.

After you install wine, you just need to run "winecfg" from the command prompt to setup wine and then you can get started getting your applications to work.

---

### Post by mello151 on 2006-09-20
Thank you very much!

---

### Post by mello151 on 2006-09-20
When I try 'winecfg' I get:
```
mel@tux:~$ winecfg
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

```
of course my X server is running

---

