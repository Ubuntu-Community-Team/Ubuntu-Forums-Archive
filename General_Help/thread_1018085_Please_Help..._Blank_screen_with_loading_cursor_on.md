---
title: "Please Help... Blank screen with loading cursor on boot"
date: 2008-12-21
forum: General Help
---

### Post by matthewm27 on 2008-12-21
PLEASE HELP...

When I boot my computer, it goes through the ubuntu loading screen, than it has a blank screen with nothing but a loading cursor. I have already tried to "dmg" (not sure if thats what its called), "startx", and nothing fixed it. I tried doing control-alt-(1, 2, etc.), and still. Please help.

Last installed program: gnome-globalmenu-applet

Resource to above: [http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23)

I need my computer to start running again, because I have lots of stuff on there that I need, including programs and settings that I do not feel like redoing.

Thanks.

---

### Post by eBoxNet on 2008-12-21
try to hit CTRL + ALT + F1 on your loading screen,after that login with your account and type 

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

this will remove some folders in order to reset your Gnome settings back to default.
After that hit CTRL + ALT + F7

hope this will work and help you get back your GUI

---

### Post by eBoxNet on 2008-12-21
ATTENTION all of your gnome settings will be wipe out !!!!
It will look like you log in for the first time on your desktop.

---

### Post by matthewm27 on 2008-12-21
Well I dont really care about my gnome settings, I have my files and Ill redo it. Thanks so much for the help (though I'm not sure if it will work). Ill post the results next.

---

### Post by matthewm27 on 2008-12-22
It didn't work:(... I really don't wanna be stuck with windows, so PLEASE help.

---

