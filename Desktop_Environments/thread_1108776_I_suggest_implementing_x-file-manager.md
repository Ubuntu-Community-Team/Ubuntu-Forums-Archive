---
title: "I suggest implementing x-file-manager"
date: 2009-03-28
forum: Desktop Environments
---

### Post by jeffus_il on 2009-03-28
I want to implement a default file manager for all the X desktops I use.
There is a system for defining a default terminal, browser, window manager, and session manager using:

/usr/bin/x-session-manager  
/usr/bin/x-terminal-emulator  
/usr/bin/x-window-manager  
/usr/bin/x-www-browser

which are links to /etc/alternatives/xxxxx

They enable you to set up the above default programs by simply defining a link.

If **/usr/bin/x-file-manager** was also defined and used by applications, one could easily set up a default X file manager.

Any support for this suggestion?

---

### Post by kerry_s on 2009-03-28
why? you already decide what file manager to use, it's not like your using your file manager of choice and when you click a folder another file manager opens.

---

### Post by jeffus_il on 2009-03-28
Ah, there are many applications that open a file manager, one for example is the archiver application which offers to open the extracted file directory after extracting, download applications which open the download directory, and more...

---

### Post by kerry_s on 2009-03-28
makes since i guess for those that use a desktop that has a default file manager.

for now there's always the work around. :)
[http://psychocats.net/ubuntu/nonautilusplease](http://psychocats.net/ubuntu/nonautilusplease)

---

### Post by T_W on 2009-03-28
Sounds similar to the Freedesktop.org Portland project.  

[http://portland.freedesktop.org/wiki/](http://portland.freedesktop.org/wiki/)

The XdgUtils ([http://portland.freedesktop.org/wiki/XdgUtils](http://portland.freedesktop.org/wiki/XdgUtils)) have some abstractions to hide desktop-specific operations like composing an email or starting a web browser.

---

### Post by jeffus_il on 2009-03-28
Interesting, xdg-open opens urls and files, maybe it knows how to open a folder, thanks.

---

### Post by jeffus_il on 2009-03-28
OK, 
> xdg-mime query filetype /home/jeffgives the result
> application/x-directoryand  
> xdg-mime default /usr/share/applications/pcmanfm.desktop  application/x-directorymakes pcmanfm the default application for opening directories
but
> xdg-open  /home/jefffails with this output
> Warning: unknown mime-type for "/home/jeff" -- using "application/octet-stream"
Error: no "view" mailcap rules found for type "application/octet-stream"
and yet above **xdg-mime** figured that it does have a mimme type **application/x-directory**

I must be missing something, any ideas?

---

### Post by T_W on 2009-03-28
I am on Hardy:

```
$ xdg-mime query filetype ~
x-directory/normal

$ xdg-mime query default x-directory/normal
nautilus-folder-handler.desktop

$ xdg-open ~

<Nautilus Pops Up, showing my home directory>

```

---

### Post by T_W on 2009-03-28
BTW I am running Gnome.

xdg-open detect Gnome and then calls 

```
gnome-open ~
```

which brings up nautilus.  I am not sure of behavior in other DEs.

You can do 

```
sh -x /usr/bin/xdg-open ~
```

to see what the script does to perform the requested action.

---

### Post by jeffus_il on 2009-03-28
Under Gnome I have the same behavior as you .
It will only open Nautilus, even if I set up pcmanfm as the default.
I will play some more and see what happens
Thanks

---

### Post by jeffus_il on 2009-03-29
It seems that the reason for differences between xdg-open behavior on different desktops is that xdg does not use it's own database but updates the databases of the desktop.

---

