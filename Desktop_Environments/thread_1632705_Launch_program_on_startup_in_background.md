---
title: "Launch program on startup in background"
date: 2010-11-28
forum: Desktop Environments
---

### Post by Apolyonn on 2010-11-28
Hey all,

I'm running Ubuntu 10.04 and I'd like Tomboy notes to initialize in the Notification area on startup.  However I don't want the screen with my notes to pop up every time I start my computer.  It's in my startup applications list, command "tomboy notes". 

Is there any way for this program to launch on startup in the background?

---

### Post by Wobblybob on 2010-11-28
try adding it to the Startup Applications as;

tomboy --tray-icon

---

### Post by Apolyonn on 2010-11-28
> **Wobblybob said:**
> try adding it to the Startup Applications as;

tomboy --tray-icon

Did not work.  Also tired:

```

tomboy notes --tray icon
tomboy notes &
tomboy &

```

---

### Post by Wobblybob on 2010-11-28
strange, I'm running a gnome desktop on 10.10 and it works for me.

---

### Post by Apolyonn on 2010-11-28
> **Wobblybob said:**
> strange, I'm running a gnome desktop on 10.10 and it works for me.

That is odd, but it's still not auto-launching in the tray area.

---

### Post by Krytarik on 2010-11-29
Hi Apolyonn,

I also have Ubuntu 10.04 and also have the same strange behaviour. After trying out some options, I found a way to manage to start Tomboy at startup as tray-icon. You have to delay the launch of Tomboy a few seconds through a script.

~/.config/autostart/tomboy.desktop

```
[Desktop Entry]
Type=Application
Name=Tomboy Notes
Comment=Take notes, link ideas, and stay organized
GenericName=Note-taker
Exec=tomboy_tray-icon
Icon=tomboy
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
```

/usr/local/bin/tomboy_tray-icon

```
#!/bin/sh

sleep 5

tomboy --tray-icon
```

---

### Post by Wobblybob on 2010-11-30
That's interesting, that must mean 10.10 starts faster [at least on my lappy] so tomboy works in startup without delaying it. Sounds like a good reason to upgrade :p

---

### Post by Krytarik on 2010-11-30
Or maybe there is a different handling of startup-programs or they implemented workaround. ;)

---

### Post by gogolink on 2010-11-30
Perhaps I'm not understanding the question right.  But did you consider adding Tomboy to a panel -- instead of to startup applications?  That's where I have it.  Starts up fine, with just the icon in panel; no pop-up window.  I also set keyboard shortcuts for new note and show all; they work fine as well.

---

### Post by Krytarik on 2010-12-01
Hi gogolink,

you have to click on the Tomboy-icon, which you added to the panel, each time after startup, right?!

That's definetely easier than to do it via the menu, but that's nevertheless what Apolyonn want to avoid to have to do: each starting it on his/her own.;)

Greetings
Krytarik

---

### Post by Apolyonn on 2010-12-01
Hey all,

Just wanted to say that I decided to just upgrade my distribution to 10.10.  went to startup applications and added the command tomboy --tray-icon, and I want to confirm that it now auto-starts in the tray without the list of notes popping up.  Krytarik, thank you for your help as well, I wish I knew how to look at scripts and debug things like that ^_^

All is well on this end.

---

### Post by gogolink on 2010-12-01
Hey Krytarik,

No, I don't click the icon after startup.  I guess I'm confused about what Apolyonn means by "initializing" Tomboy.  I just need it running when I create a note, or when I look for an existing note.  Clicking on the Tomboy icon --on the panel-- will give me both options.

More recently, I simply defined keyboard shortcuts (system > preferences > keyboard shortcuts: add): I use F1 to create a new note (Name: Tomboy; command: tomboy --new-note), and F2 to search my notes (name: Tomboy search all; command: tomboy --search).

Am I completely misunderstanding something?

---

### Post by Krytarik on 2010-12-01
Actually I don't use Tomboy at all. I guess Apolyonn just wants quicker access to his/her notes without having to start Tomboy manually each time.

---

