---
title: "Install a GUI to the server edition"
date: 2009-01-05
forum: Desktop Environments
---

### Post by HeroXx on 2009-01-05
I know, I know the server should be a without a GUI but I have a few people that share the cost of the server and would much prefer to run Windows. We came to a compromise to get a GUI installed for Ubuntu and VNC.

We do not have physical access to the server so we would need to be able to install of all of the software over SSH.

I have been searching and searching and I am just getting broad results returned, is there anyone that has done this before or knows of a guide?

---

### Post by lykwydchykyn on 2009-01-05
I'm kind of surprised a search turned up nothing, this question gets asked about once a week in the server forum.

Anyway, this command gets you the full GNOME desktop with all software, etc:
```

sudo apt-get install ubuntu-desktop

```

If you just want a GUI and not all the stuff, install xorg and whichever window manager or desktop environment you want.  Icewm, fluxbox, or jwm are nice for servers.

---

### Post by ibutho on 2009-01-05
The server version uses the same repos as the desktop versions, so you can use apt-get to install ubuntu-desktop, kubuntu-desktop, xubuntu-desktop or install window managers like fluxbox.

---

### Post by jowilkin on 2009-01-05
THe above command will get you the ubuntu gnome desktop.  You can also get KDE with ```
apt-get install kubuntu-desktop
``` or XFCE with ```
apt-get install xubuntu-desktop
```

---

### Post by HeroXx on 2009-01-05
Running something like xorg would that mean the GUI would be running constantly with the ability to VNC?

Also the first result I got on google was someone having problems running xorg without a screen.

---

### Post by lykwydchykyn on 2009-01-05
> **HeroXx said:**
> Running something like xorg would that mean the GUI would be running constantly with the ability to VNC?

Also the first result I got on google was someone having problems running xorg without a screen.


yes.  And any of these options will install xorg as a dependency.

it works fine without a monitor, trust me on that.

---

### Post by HeroXx on 2009-01-05
Cheers for your help getting me this far, I have installed ubuntu-desktop but I am having problems connecting via VNC. I have just ran through the steps next to me on a laptop but I can't figure out how I could enable remote desktop without being next to the server with a mouse and keyboard.

Any ideas?

And how would I know if Gnome is running?

---

### Post by HeroXx on 2009-01-05
Cracking on now I have found that you can enable/disable it buy typing 
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true

But I don't have /desktop/gnome :/

---

### Post by jbuturff on 2009-01-05
One of my favorite tricks is running XDM over VNC, like in this article.

This will enable you to have multiple users via VNC rather than just one on the desktop.


[http://homepage.ntlworld.com/daniel.rigal/xdmvnc.html](http://homepage.ntlworld.com/daniel.rigal/xdmvnc.html)

---

