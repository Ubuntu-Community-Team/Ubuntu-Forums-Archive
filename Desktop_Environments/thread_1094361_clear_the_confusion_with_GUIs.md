---
title: "clear the confusion with GUIs?"
date: 2009-03-12
forum: Desktop Environments
---

### Post by nightrider.36 on 2009-03-12
**The issue:**Why doesn't my laptop's wifi work when I use *Windowmaker* or a similar type of window manager? The hardware is enabled but the Windowmaker doesn't detect it. *GNOME* is doing something that enables my laptop's wifi to find an access point. How can I get *Windowmaker* to do the same thing?  

**My attempts**
Not many really because I don't understand how to enable the laptop's wifi from the command line. I used some commands that I found in a book called, *Ubuntu Linux Toolbox* and was unsuccesful. *Sudo iwconfig blah-blah*(too much to type and I'm sure you all get the idea)..., nothing worked. What I've done is to log on to GNOME first to get wifi to work, log out and start a Windowmaker session but that's annoying.

**My problem.**
I don't think I understand the difference between an environment like *GNOME* and a window manager like *Windowmaker*. What's doing what?  Where can I find resources to help me fix it?

Thanks.

---

### Post by Vadi on 2009-03-12
NetworkManager is probably missing on the Windowmaker and that's why wifi doesn't work, while the Gnome desktop uses NetworkManager for wifi by default.

Maybe see if you can get NetworkManager to run in Windowmaker?

---

### Post by kellemes on 2009-03-12
<youreditor> ~/.xinitrc

```
#!/bin/sh
nm-applet &
exec wmaker
```

---

