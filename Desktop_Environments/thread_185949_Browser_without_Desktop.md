---
title: "Browser without Desktop"
date: 2006-06-01
forum: Desktop Environments
---

### Post by pradeep79 on 2006-06-01
Hi folks, I just wanted to ask a simple yet silly question: Is there anyway you can run a browser like firefox without a desktop, i.e can you run it from a server version from the shell. Are there any graphical applications that can be run from the shell without the need to open a desktop.

---

### Post by Ramses de Norre on 2006-06-01
Hmm you'll need X running, and X will need his own virtual terminal (like ctrl+alt+F7). So it won't be better then a normal desktop I think.
There are text based browsers for cli though.

---

### Post by jonibo on 2006-06-01
You don't strictly need a desktop, but you do need an X running... something along the lines of:

startx /usr/bin/firefox

or similar should do the trick.  It won't give you a window manager though.

Check out:

man startx

for more info.

Someone else can say if you can get this working with a framebuffer....

---

### Post by Seq on 2006-06-01
I believe links has a framebuffer mode that allows you to browse from the console. I'm on windows at work, but I will check when I get home.

---

### Post by Hanj on 2006-06-01
You will need X to run graphical applications. However, you don't need a full desktop environment, like Gnome or KDE. For a server you might want something lighter and less resource-consuming. Check out windowmaker and fluxbox for instance, they're in the repos.

[Edit]Wow, beaten by three posts. Jonibo, that's pretty cool, didn't know you could do that. [/Edit]

---

### Post by bluevoodoo1 on 2006-06-01
"lynx" is a command line based browser. Very handy if you ever have a terrible "X catastrophe."

---

### Post by Zed on 2006-06-01
There are several text-mode browsers, and several graphical ones you can run without X.

```

aptitude search w3m links

```

[Links home page](http://artax.karlin.mff.cuni.cz/~mikulas/links/)

And check out the ratpoison window manager if you want to run X applications without looking like you're in a window manager.

---

### Post by Seq on 2006-06-01
[QUOTE=Seq]I believe links has a framebuffer mode that allows you to browse from the console. I'm on windows at work, but I will check when I get home.[/QUOTE]
Alright, I just did some looking. I was thinking of links2. Aside from the (very good) suggestions of lynx, or the suggestions to just install X11 (which you probably don't need on a server), there is links2 which has a graphical framebuffer mode.

> apt-get install links2 gpm

gpm is needed if you are on an actual console.

> links2 -g

If you are on a console, you will have a framebuffered window (if supported.. I'm not sure of any differing features between the standard and server kernels) with a mouse controlled via gpm. If connected via ssh, it will launch the X11 version.

Now, a few notes since I'm too lazy to do all the required checking: it may need X11 libs, but not actually a runnable X11. It is possible the server kernel does not have a nice framebuffer to work with. It is possible it does not work without a mouse attached (I had an error without having gpm installed, though it may with with gpm installed, but no mouse attached). I checked this on a regular ppc ubuntu dapper installation, not a server edition.

That is, after all, only if you want a pretty console-based browser. Otherwise either browse with lynx/links, or from your workstation.

---

