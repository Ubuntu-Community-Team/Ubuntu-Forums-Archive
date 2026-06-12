---
title: "Type command every time?"
date: 2013-03-02
forum: Desktop Environments
---

### Post by Asa J on 2013-03-02
I installed Ubuntu 12.10 and suddenly the internet has no answers. :shock:

Trying to run Arduino 1.0.3, apparently it's a shell script. I can run it from terminal with sudo, but not double clicking the script in my home folder, which seems to be what everyone else is able to do.  I just want a shortcut!! I keep switching between Gnome and Gnome classic but neither is working for me. Also, why can't I make a launcher or a shortcut in Gnome 3? This whole Ubuntu 12.10 is sealed up tighter than a frog's anus.

---

### Post by Frogs Hair on 2013-03-02
In classic it is possible to create a launcher using the main menu and then drag it to the desktop. In the shell you can add the launcher to favorites on the left side.

---

### Post by tgalati4 on 2013-03-02
You might have to add executable privilege to the script:

```
sudo chmod +x arduino.script
```

I have 1.03 installed on another laptop, but I'm too lazy to boot it and find out.

You could run the script with gksudo arduino.script put inside a launcher icon.  I don't think you need sudo to program an arduino, but it's been a few weeks since I last hacked on mine.

---

