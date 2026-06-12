---
title: "VMWare with no window manager on second X session?"
date: 2007-10-31
forum: Desktop Environments
---

### Post by mjwalfredo on 2007-10-31
First off, here is what I have:  
Fiesty Fawn running Gnome as my desktop.  Nothing fancy.

What I would like to have:  
I want to be able to switch to virtual terminal 1 and start another X session with vmware running fullscreen as the only application.  I'd like to be able to switch back and forth between the two X sessions as well.

I am hoping that this will allow me to have Ubuntu and Windows XP running side by side.


Right now when I type startx -- :1, another gnome session loads up in the second terminal.

What do I need to edit to have only vmware start?  There is no .xinitrc in my home directory.  Should I edit /etc/X11/.xinitrc?  How should I edit it to get it to do what I want?  Thanks

(I realize those path names and filenames my not be 100% correct, I am at work and away from my box so I guessed)

---

### Post by maybeway36 on 2007-10-31
You can make a file called "~/vmwarex" (regular text file) that looks like this:
```
#!/bin/sh
metacity&
exec /usr/bin/vmware-server
```
I'm not sure what the VMWare Server executable in /usr/bin is named, so make sure to change it.
Then type in a terminal:
[CODE]startx /home/your-name/vmwarex -- :1

P.S. The file you make doesn't have to be named vmwarex, you can call it anything you want.[CODE]

---

### Post by mjwalfredo on 2007-10-31
You da man maybeway!  I think I am going to try it without metacity though.  I don't want any window manager since I will be running vmplayer fullscreen.  I guess it doesn't matter either way since metacity is very light I am guessing.  We'll see.

---

