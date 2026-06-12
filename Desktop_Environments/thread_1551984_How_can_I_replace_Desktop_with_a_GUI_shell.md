---
title: "How can I replace Desktop with a GUI shell?"
date: 2010-08-13
forum: Desktop Environments
---

### Post by EduardoMartins on 2010-08-13
Hi,

I would like to configure my Ubuntu as to start Gnome without a Desktop; instead, I would like to have a graphical shell taking the whole screen, but keeping all the other functionalities of the GUI.

It doesn't really have to be Gnome - I would gladly take any GUI with the above-mentioned description that would open Firefox, Amaya and Calibre.

I am trying to save some memory with a feeble Acer Aspire One that is solely used for browsing the web (Firefox), editing webpages (Amaya), and creating .mobi files.

Any ideas on how to replace the Desktop with a shell or taking a different approach?

Thanks,

Eduardo

P.S.: I looked at the Ubuntu Netbook Remix and the soon-to-be-released Gnome Shell, but they are not what I am looking for!

---

### Post by kerry_s on 2010-08-13
> I am trying to save some memory with a feeble Acer Aspire One that is solely used for browsing the web 

it can do more then that, your just limiting yourself.

you can create your own xsession for a custom setup like that.

---

### Post by Spice Weasel on 2010-08-13
Why don't you just start up using a lightweight window manager, and then set up PCManFM to show icons on the root window for you to pick a program? A shell isn't really needed if all you are going to be doing is using three programs.

---

### Post by ender4 on 2010-08-13
I have never actually tried it, but I believe that you could edit (or create if it does not exist) the .xinitrc file in your home directory, so that it would only run the programs that you wanted.  Each program except the last (which should be some sort of window manager) should be in the background.  A sample that starts firefox and an xterm might be:

```

firefox & 
xterm &
x-window-manager

```

This would probably need some tweaking, and might not work at all.  But my guess is that the solution is something similar.

---

### Post by EduardoMartins on 2010-08-13
Thanks for all the feedback!

@kerry_s &#8594; I'll look into it.

@Spice Weasel &#8594; I was just watching a Lubuntu demonstrations on Youtube, actually! The option for a shell instead of, say, Nautilus or another graphical interface is that I have the impression a text-based way of browsing files is way lighter (and I actually enjoy using shell commands).

@ender4 &#8594; I am trying not to have to start the entire Gnome desktop environment when running any of the 3 mentioned programs - I want the GUI, but keeping it in a minimum usage.

So, when you say "that it would only run the programs that you wanted", doesn't it mean always starting them whenever I use the computer? I do not intend to use the 3 programs everyday (e.g.: I won't be creating ebooks everyday).

From what I read in the Lubuntu description, things are not as tightly integrated as in Gnome, as to make running programs a low-consumption process. Still, I'll have to try it for myself, test my programs and see if I can eliminate the Desktop (maybe with the method kerry_s suggested).

---

### Post by kerry_s on 2010-08-13
how about just starting the gnome-panel?

gksudo gedit /usr/share/xsessions/custom.desktop

put:

```
[Desktop Entry]
Encoding=UTF-8
Name=Custom
Comment=
Exec=gnome-panel
TryExec=gnome-panel
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gdm
```

log out & select it in the session menu see if it works.

---

