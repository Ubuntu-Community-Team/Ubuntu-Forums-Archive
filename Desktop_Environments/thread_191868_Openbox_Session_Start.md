---
title: "Openbox Session Start"
date: 2006-06-08
forum: Desktop Environments
---

### Post by open_coder on 2006-06-08
I have Dapper installed and I am running Openbox. I want to set up a session file so that pypanel starts running when i log in, and so that the background gets set by itself. How can I accomplish this?

--Alex

---

### Post by Sutekh on 2006-06-08
Are you using Openbox by iteself or GNOME with Openbox as the window manager?

Are you using the GNOME display manager - GDM to log in, or are you starting Openbox with *startx?*

---

### Post by open_coder on 2006-06-08
[QUOTE=Sutekh]Are you using Openbox by iteself or GNOME with Openbox as the window manager?

Are you using the GNOME display manager - GDM to log in, or are you starting Openbox with *startx?*[/QUOTE]
I am using Openbox by itself and logging in with GDM.

---

### Post by open_coder on 2006-06-08
anybody?

---

### Post by Sutekh on 2006-06-09
Sorry to keep you waiting.

[quote=open_coder]I am using Openbox by itself and logging in with GDM.[/quote] 
I hoped you'd say this.  You should be able to accomplish this using a custom ~/.xsession file.  The GDM will look for this file, when you log in.

Details on using it here

[Ubuntu Wiki - Openbox - Configuration (.xsession)]("https://wiki.ubuntu.com/Openbox#head-a20af337d65d97f3df1aed6739d4df8028b104e0")


For running pypanel you should use the command (in the xsession file)
```
pypanel &
``` 
For a background you should use [feh]("http://packages.ubuntu.com/dapper/graphics/feh") from the universe repository.  Again this is a sample command for using feh in the xsession file. 
```
feh --bg-scale /home/user/desktop.jpg
```There is much more in the Openbox wiki page, including a random wallpaper script (very cool!)


If you want more information on .xsession files, try the [Ubuntu Wiki - Custom XSession]("https://wiki.ubuntu.com/CustomXSession") page too.

Hope this helps out.  Openbox is great, but you need to invest some time to get the best from it.

---

