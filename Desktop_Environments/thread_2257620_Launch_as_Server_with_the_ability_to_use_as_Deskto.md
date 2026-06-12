---
title: "Launch as Server with the ability to use as Desktop"
date: 2014-12-21
forum: Desktop Environments
---

### Post by dennis40 on 2014-12-21
Hello again, 

Now I was wondering if I can run my ubuntu 14.04 desktop installation to boot as the server variant? With the ability to press Ctrl Alt F7 to launch the gui.
So i normally use the server as a modded minecraft server for my kids to play with their friends so it could run in the server modus. 
But when for example I need to google something while working could I then with a simple command launch the Gui?

I really hope this could be possible, because I don't need the Desktop Gui running all the time

---

### Post by steeldriver on 2014-12-21
Ctrl-Alt-F7 normally just switches to virtual terminal #7 - it doesn't actually control whether a GUI is running in that VT or not

You basically have 2 options: run with a display manager (such as lightdm) but configure it not to start automatically (e.g. using a lightdm.override file in /etc/init), then start it manually as required by logging in at the CLI and then executing

```

sudo service lightdm start

```

or run without a DM at all, and just start the user's desktop session using

```

startx

```

after logging in at the CLI.

---

