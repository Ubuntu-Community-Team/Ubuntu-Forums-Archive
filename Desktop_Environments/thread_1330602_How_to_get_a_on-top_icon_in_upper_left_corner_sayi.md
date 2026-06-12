---
title: "How to get a on-top icon in upper left corner: saying 1...5 for workspace?"
date: 2009-11-18
forum: Desktop Environments
---

### Post by frenchn00b on 2009-11-18
How to get a on-top icon in upper left corner: saying 1...5 for workspace, and after few secs to vanish?

I use xdotool to switch to next workspace:

```
 
# like under fluxbox
 <Key mask="CA" key="Left">exec: let i="`xdotool get_desktop`-1" ; xdotool set_desktop $i</Key>
 <Key mask="CA" key="Right">exec: let i="1+`xdotool get_desktop`" ; xdotool set_desktop $i</Key>
 <Key mask="A" key="S">exec: let i="`xdotool get_desktop`-1" ; xdotool set_desktop $i</Key>
 <Key mask="A" key="D">exec: let i="1+`xdotool get_desktop`" ; xdotool set_desktop $i</Key>



```

gnome has that, itis in the middle of the screen.

---

### Post by frenchn00b on 2009-11-18
I found this code, but it put thousand workspaces icons ... not working :( 

```
 kdialog --passivepopup `xdotool get_desktop` &
```

---

