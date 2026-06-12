---
title: "Remote desktop *without* disabling compiz?"
date: 2010-02-15
forum: Desktop Environments
---

### Post by CDrewing on 2010-02-15
Hi,

is there a way to have a *graphical* remote desktop connection without having to disable compiz effects or to have to replace it with metacity?

It's really annoying!

Greetz
Christian

---

### Post by stinkeye on 2010-02-15
I don't have to disable compiz.
I use this guide to connect.
[**_[COLOR="DarkRed"]Connect to a remote Linux desktop with x11vnc and Gtk VNC[/COLOR]_**]("http://www.ghacks.net/2010/01/24/connect-to-a-remote-linux-desktop-with-x11vnc-and-gtk-vnc/")

---

### Post by krunge on 2010-02-15
> Hi,
is there a way to have a *graphical* remote desktop connection without having to disable compiz effects or to have to replace it with metacity?

The cmdline tool x11vnc (apt-get install x11vnc) allows this, use its "-noxdamage" option to workaround the problems with compiz (and Xorg and/or nvidia drivers):
```
x11vnc -noxdamage
```
If you run that command in a terminal from inside your desktop, that should export the desktop via VNC.

If you have questions about setting a VNC password or enabling encrypted connections, feel free to ask.

---

### Post by Boondoklife on 2010-02-15
You can also just set the nodamage option in gconf-editor

/desktop/gnome/remote_access/disable_xdamage <true>

This will allow you to view the desktop and it will update fine. Do be aware that it is very bandwidth hungry with this setting.

---

### Post by perevera on 2010-04-03
Ok, I am facing a similar problem.

I have a barebone running Ubuntu Karmic Koala that I want to control from my desktop (Ubuntu as well) with Remote Desktop Viewer, or from my laptop (Windows XP) with VNC Viewer.

In any case, it does not work unless I launch in the server the known command: 'metacity --replace'.

Now, I want to deactivate Compiz and leave Metacity as default, better if I don't have to uninstall Compiz.

So, the question is: how can I launch that command at startup?

I tried setting it in the /etc/rc.local file, with no luck.

---

### Post by Boondoklife on 2010-04-03
Just disable the desktop effects and then you will not have an issue. You can install ubuntu-tweak and there is an option in there to use metacity for compositing if that is what you are looking for.

---

### Post by stchman on 2011-03-29
The checking the box disable_xdamage worked 100%.  Yes, it is bandwidth hungry, but it works.

Thanks.

---

