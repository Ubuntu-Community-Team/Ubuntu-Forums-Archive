---
title: "Default WM"
date: 2005-11-02
forum: Desktop Environments
---

### Post by christooss on 2005-11-02
How can I change that computer would boot in IceWM and not in GNOME. Yes I have IceWM installed :P

I know that I can change in gdm but this doesn't work with me so I have to edit one of configuration file but I don't know which.

I thank ou for all the anwsers

---

### Post by tmadsen on 2005-11-02
I tried this out, but _without_ luck. Thought it might lead you on to something, as I'm not familiar with iceWM whatsoever.

first:

```
sudo cp /usr/share/gnome/default.session ~/.gnome2/session
```

then:

```
sudo nano ~/.gnome2/session
```

found the line that reads:

> 0,RestartCommand=gnome-wm --sm-client-id default0

and changed it to this:

> 0,RestartCommand=icewm --sm-client-id default0

This caused icewm to freeze up in some way, and display the gnome wallpaper and such.

I tried handling this by: Applications -> System Tools -> Configuration Editor -> apps-> nautilus -> preferences -> uncheck show desktop

But without any luck. Maybe if you're smart you can make this work, I'm not :)

---

### Post by Iandefor on 2005-11-02
How is it that IceWM doesn't work? Like, what happens when you try to login with it? If you're just looking for a lightweight WM, I've found that Fluxbox works well.

---

### Post by christooss on 2005-11-02
No the problem is that in gdm when I choose iceWM beacause I have some problems with one of files called .dmrc it doesn't login in IceWm but in GNOME. So I would like to fix it through editing right file.

tmadsen I will try this and I will report to you.

---

### Post by Dr. Nick on 2005-11-02
[http://ubuntuforums.org/showthread.php?t=80099](http://ubuntuforums.org/showthread.php?t=80099)

Ew the nasty dmrc file, I had that to and the above thread fixed it. It should work off the GDM so fixing that file may fix it all for you

---

### Post by christooss on 2005-11-06
I managed to run icewm with creating .xsession file and there I put

```
exec icewm
```

And then when I wanted to go in gnome I just changed that line to

```
exec gnome-session
```

But now I solved that thing with dmrc. Thanks DR. Nick

---

