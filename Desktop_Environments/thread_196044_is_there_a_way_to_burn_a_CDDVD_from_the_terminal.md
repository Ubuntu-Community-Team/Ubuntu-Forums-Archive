---
title: "is there a way to burn a CD/DVD from the terminal ?"
date: 2006-06-13
forum: Desktop Environments
---

### Post by syxbit on 2006-06-13
i want to burn stuff over SSH
anyone know of a program or way to do this on the terminal ?
thanks

---

### Post by az on 2006-06-13
Put everything you want in a directory somewhere and make an iso out of it:

mkisofs -o cd.iso -R /home/me/iso/
 
and then burn it.

cdrecord -v speed=24 dev=/dev/hdc cd.iso


Read the mkisofs and cdrecord manpages.  I am not in front of my linux box right now.

---

### Post by HankB on 2006-06-13
What about tunneling X over ssh? Start your remote session with

```
ssh -X <remote host>
```

And any X applications on the remote will display on your local server. I just tried running k3b and it displays remotely. I don't know offhand how to run the built in burning programs, but you just have to figure out what programs run. Perhaps running nautilus (if you use gnome) would make those accessible.

Of course as azz mentioned you do have access to command line utilities that can do this without any GUI. To the best of my knowledge, the GUIs just invoke these programs in the background anyway. But some times it is nice not to have to learn the commands and arguments and just poke at a GUI. ;)

-hank

---

### Post by az on 2006-06-13
I used cdw and burn ages ago.  You can use them to make life easier.

install the package named "burn" and you get a nifty command-line utility to burn cds.  It's a python wrapper to all the cdr tools.

cdw is a curses-based cdburning application.  I don't know if it works well with HAl and dbus....

---

### Post by HankB on 2006-06-13
[QUOTE=azz] and dbus....[/QUOTE]

With apologies for thread hijack... [-X 

What's dbus?

I'm trying to run xine on a dedicated x server. No desktop manager, just using startx and running xine from a script passed to xinit on the command line. I get these messages about every ten seconds in the window  that I start the X server from. Earlier when I was running a dual headed server and running gxine on display :0.1, I had the same result.

```
gnome-screensaver-Message: Failed to connect to the D-BUS daemon: Unable to determine the address of the message bus
```

I suppose I can just redirect this to /dev/null, but it might be telling me that something else is going on behind the scenes that I should stop.

thanks,
hank

---

