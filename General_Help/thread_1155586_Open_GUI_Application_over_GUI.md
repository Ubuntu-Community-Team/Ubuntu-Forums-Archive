---
title: "Open GUI Application over GUI"
date: 2009-05-10
forum: General Help
---

### Post by xHero on 2009-05-10
How do I run a GUI application from SSH?  If I'd like to start Firefox or Transmission remotely, is this possible?

xHero

---

### Post by pytheas22 on 2009-05-11
It's pretty easy.  You first need to use the -X argument when starting your ssh session to enable X11 forwarding (or if you're using an ssh client like Putty, enable X11 forwarding in the options).  For example:
```

ssh -X user@hostname
```

Then just type the name of the program you want to start, e.g.:
```

firefox
```

Keep in mind that this may not work well over slow connections; if you don't have a lot of bandwidth on both ends of the connection, you may want to consider using VNC or FreeNX instead, which are a bit faster.  You can also use the -C flag with ssh to compress data, saving bandwidth.

Also keep in mind that the computer you're connecting from (i.e., the one you're sitting in front of) needs to have an X server installed and running in order for this to work.  Any Linux distribution with a GUI should have X, and I think the most recent version of Apple's OS X also comes with X installed by default.  On a Windows machine, you need to install X separately; unfortunately I'm not sure how to do that, but I'm sure Google could tell you.

---

### Post by xHero on 2009-05-11
I tried that, however it opened the app on my end, not theirs.  I do not want to open the application on my computer, but rather the remote machine.

---

### Post by pytheas22 on 2009-05-11
Oh, apologies.  I think you can still do this, but I never have personally.  You would need to tell the system which screen to launch the application on, and you would need to make sure you have permission to write to that screen.  I'm not sure what the syntax or arguments are for specifying the screen, however.

A much easier way to do this would be just to use VNC or FreeNX and connect to take control of the Gnome (or whatever) session remotely.

---

