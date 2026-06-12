---
title: "Compiz desktop problem."
date: 2009-03-06
forum: Desktop Environments
---

### Post by bhishan on 2009-03-06
I am using Ubuntu 9.10. I was trying to put different wallpapers to different sides of the cube by compiz. I played around with some settings. My wallpaper changed but, now I can not right click on my desktop. I also can not see the icons on my desktop. So I uninstalled compiz. The cube is gone, but the right click problem still persists. Can anyone help?

---

### Post by UbuntuNerd on 2009-03-06
did you change any settings in "nautilus" maybe the one that says "show desktop"?

---

### Post by bhishan on 2009-03-06
> **UbuntuNerd said:**
> did you change any settings in "nautilus" maybe the one that says "show desktop"?
yes, I think so.

---

### Post by UbuntuNerd on 2009-03-06
go to the terminal and type this:
```
gconf-editor
```
when the Nautilus window opens on the left navigate to: apps > nautilus > preferences:
After you select “preferences,” look on the list on the right until you see the option “show_desktop” and make sure is cliked.

---

### Post by thedavis on 2009-03-07
> **UbuntuNerd said:**
> go to the terminal and type this:
```
gconf-editor
```
when the Nautilus window opens on the left navigate to: apps > nautilus > preferences:
After you select “preferences,” look on the list on the right until you see the option “show_desktop” and make sure is cliked.

Ihave the same problem, I run the gconf-editor, the show_desktop option is marked, but no desktop, I must do ALT+F2 and launch "nautilus" to get the desktop icons, but after restar, the same issue :(:( 

I'm stuck :(:(

Any idea? 

Thankssss!!

---

### Post by bhishan on 2009-03-07
> **UbuntuNerd said:**
> go to the terminal and type this:
```
gconf-editor
```
when the Nautilus window opens on the left navigate to: apps > nautilus > preferences:
After you select “preferences,” look on the list on the right until you see the option “show_desktop” and make sure is cliked.
thanks a lot. It worked after a restart.

---

### Post by UbuntuNerd on 2009-03-07
> **thedavis said:**
> Ihave the same problem, I run the gconf-editor, the show_desktop option is marked, but no desktop, I must do ALT+F2 and launch "nautilus" to get the desktop icons, but after restar, the same issue :(:( 

I'm stuck :(:(

Any idea? 

Thankssss!!

have you try reinstalling your desktop if you want to give a try type this in a terminal:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by thedavis on 2009-03-07
> **UbuntuNerd said:**
> have you try reinstalling your desktop if you want to give a try type this in a terminal:
```
sudo apt-get install ubuntu-desktop
```

Thanks UbuntuNerd, the ubuntu-desktop it was installed, but I did a reinstall via synaptic and after first restart it's seems working fine :)

Many thanks ;)

---

