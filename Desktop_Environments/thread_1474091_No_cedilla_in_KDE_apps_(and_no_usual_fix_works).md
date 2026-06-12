---
title: "No cedilla in KDE apps (and no usual fix works)"
date: 2010-05-05
forum: Desktop Environments
---

### Post by krisdevill on 2010-05-05
Hello everyone !

I experience a weird problem with my newly installed Ubuntu 10.04.

I use a us international keyboard with dead keys. Every of my GTK apps do a ç when I press the ' + c keys. but my KDE apps don't.

As I had the same issue with my 9.10 build, I tried to replace every &#263; from the /usr/share/X11/locale/en_US/Compose with ç, but it didn't work, even after rebooting or creating a new user. I'm stuck with the &#263;.

Does someone have any idea on how I could fix that ?

Thanks !

---

### Post by leonardopsantos on 2010-05-12
Same thing here with Lucid.

Edited /usr/share/X11/locale/en_US.UTF-8/Compose, did the replacing and all QT applications still give me &#263; instead of ç.

Deadkeys are working, if I type '+e I get é.

Tried to log out and restart. Funny thing is that this fix used to work since 6.10 (my first Kubuntu install).

Maybe is a X11 problem ? Lucid doesn't have an xorg.conf and X11 might need an InputDevice section ?

---

### Post by joelteixeira on 2010-05-14
The same here guys, there is a long time now I always the same fix. This time, it did not work. Any ideas?

---

### Post by Zorael on 2010-05-15
I don't know how to solve this, but I can offer one thing to try that could help, and another alternative that works around the issue.

First, try entering this in a terminal, and then log out and back in or reboot. See if it works as you want it to after that. (sort of unlikely.)
```
$ im-switch -s default-xim
```

Second, you could instead set up a Compose key, and use compose+,c to get ç. You can define a Compose key in System Settings -> Regional & Language -> Keyboard Layout. You have to first pick Enable keyboard layouts to make the options in the Advanced tab available. Then scroll down to the Compose Key Position section in there and pick a key.

---

### Post by mailboxbr on 2010-05-20
Hey, Zorael!!! You 1st solution worked for me :))

All the previous fixes for Kubuntu did not work for me in Lucid (KDE apps). But "im-switch -s default-xim" did the job :)


Thanks!
Leo

---

### Post by joelteixeira on 2010-05-23
Fixed mine as well, thank you very much! You rock.

---

