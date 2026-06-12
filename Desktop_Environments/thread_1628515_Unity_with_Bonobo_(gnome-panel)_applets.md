---
title: "Unity with Bonobo (gnome-panel) applets?"
date: 2010-11-22
forum: Desktop Environments
---

### Post by unimatrix on 2010-11-22
Will it be possible to use the vast amounts of pre-existing gnome-panel applets on the new Unity panel?

---

### Post by ectospasm on 2010-11-23
I'm curious to know this too.

---

### Post by aaaantoine on 2011-03-29
I've heard "no", but I'll be sad if I can't add the System Monitor applet to the Unity top bar.

I like to know approximately what my system has been doing over the past minute.

---

### Post by zipperback on 2011-06-01
No you cannot use gnome-panel applets directly in unity.
You can however use gnome panel at the same time as unity and therefore you can use the applets via that.

Press alt-f2, then enter gnome-terminal.

now enter:  gnome-panel &

This will start the gnome panel interface for you, and you can have this on screen at the same time as unity.

Now enter:  exit

This will close your terminal window and the panel will stay running.

If you want it to start when you login, you can add it to the startup applications, press alt-f2 and enter:  startup applications

You can then add gnome-panel to list of applications that will start automatically.

I should probably mention that this may only work on 11.04 and not any future versions due to the fact that unity is becoming the standardized interface for Ubuntu.

- zipperback
:popcorn:

---

### Post by zipperback on 2011-06-01
If you are looking to get system information displayed, perhaps you might want to take a look at using Conky, it's available from the repositories and is pretty powerful.

Check out the ubuntuforums.org thread on the subject.
[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky")

- zipperback
:popcorn:

---

