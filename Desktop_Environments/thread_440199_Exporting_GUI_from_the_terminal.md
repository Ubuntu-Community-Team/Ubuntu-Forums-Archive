---
title: "Exporting GUI from the terminal"
date: 2007-05-11
forum: Desktop Environments
---

### Post by donatell0 on 2007-05-11
I have these issues about GUI. They oddly do not appear in Fedora.

1) I can't "sudo -i" and then open applications that require a GUI.
2) I can't "su <another user>" and then open GUI applications.

I want to be able to do these things. I think the matter is to just set something in some config files.
Could someone help me?

---

### Post by EndPerform on 2007-05-11
What errors are you getting?  For example, right now I can do a sudo kate and the Kate editor pops up for me without a problem.

---

### Post by FuturePilot on 2007-05-11
If you need to launch an application as root use
```
gksudo app_command_here
```
For example if you need to run Gedit as root use```
gksudo gedit
```
You should never use sudo to launch GUI applications
If you're using Gnome use gksudo, if you're using KDE use kdesu
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by EndPerform on 2007-05-11
Ok, why shouldn't sudo be used?  That's a first for me...

---

### Post by CameO73 on 2007-05-11
[This page]("http://www.psychocats.net/ubuntu/graphicalsudo") explains it quite well.

Long story short: most of the time you could just use **sudo **for graphical applications, but **gksudo** (or **gksu**) is safer.

---

### Post by donatell0 on 2007-05-11
> **CameO73 said:**
> [This page]("http://www.psychocats.net/ubuntu/graphicalsudo") explains it quite well.

Long story short: most of the time you could just use **sudo **for graphical applications, but **gksudo** (or **gksu**) is safer.

Thanks for the link you gave me, it explained quite a lot things to me. But it still does not solve my problem. I want to run my applications as another normal user, not as root. 

For example, what i want to do is:
```

su jim
firefox &
```

With my current settings if I do this, I get the following messages and no firefox:
```

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firefox-bin:17452): Gtk-WARNING **: cannot open display: 
```

---

### Post by CameO73 on 2007-05-14
A quick search for 'Xlib: connection to ":0.0" refused by server' on these forums pointed me towards [this thread](http://ubuntuforums.org/showthread.php?t=437646&highlight=Xlib%3A+connection+to+%3A0.0+refused+by+server). The solution mentioned in that thread seems promising... Let me know if it worked for you!

---

