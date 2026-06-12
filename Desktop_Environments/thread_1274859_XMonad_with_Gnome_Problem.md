---
title: "XMonad with Gnome Problem"
date: 2009-09-25
forum: Desktop Environments
---

### Post by abarilla on 2009-09-25
I have Xmonad setup with Gnome following the guide in the Xmonad wiki including disabling Nautilus.  However, when I first login, I get numerous Nautilus windows repeatedly opening up.  I have to open up a terminal and run 'killall nautilus' repeatedly until new ones stop opening up and then they'll slowly close one by one.

Any ideas on what's going on?

---

### Post by deadguy on 2009-10-02
I get the same problem.  Also, I can't open any nautilus file browser windows until killall nautilus fails with "nautilus: no process found".  Then it seems to work fine.

---

### Post by deadguy on 2009-10-02
duplicate

---

### Post by steinarhugi on 2009-10-23
I had the same problem on Ubuntu 9.10 Karmic Beta, numerous nautilus ("File manager...") processes piling up. Waiting for a minute before executing killall closed all of them.

I solved the problem by removing Nautilus from required components.

```
gconftool --type string --set /desktop/gnome/session/required_components/filemanager ""
```

Regards,
Steinar Hugi

---

