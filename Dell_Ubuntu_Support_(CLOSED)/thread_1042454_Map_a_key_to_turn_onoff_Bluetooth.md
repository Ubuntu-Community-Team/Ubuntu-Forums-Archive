---
title: "Map a key to turn on/off Bluetooth"
date: 2009-01-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by larainzlo07 on 2009-01-17
I am currently running Ubuntu 8.10 on my Dell Mini 9 and I am wondering if anyone has successfully mapped a key to turn on/off their bluetooth. I have the Airplane Mode program that lets you do this but I would prefer to not have to mess with that everytime to turn it on/off.

---

### Post by ajmorris on 2009-01-18
hi there,
this is very accomplishable. Assuming you have the x11-utils package installed (installed by default from a live/alternate cd install)
run:
```
xev
```

Press the key combination you want for your bluetooth.
Grab the keycode from the output in the terminal you run xev from,
then open up ~/.Xmodmap in a text editor of your choice. 

add a line like this:
```
keycode # = XF86Launch0
```
where # is the keycode number that xev gave you.
save the file, then load the new Xmodmap config file through xmodmap:
```
xmodmap ~/.Xmodmap
```

then open up gconf-editor and navigate to:
apps --> metacity --> keybinding_commands

Change the command_1 value to the command you are using to switch between on/off mode for your bluetooth.

Then navigate to apps --> metacity --> global_keybindings

Change the run_command_1 value to XF86Launch0

then restart your gnome settings daemon (or reboot your pc)

and pressing your bluetooth key combination should enable/disable your bluetooth :)


P.S The above is assuming that you are using:
1) The gnome Desktop Environment
2) The default gnome Window Manager - metacity -

AJ

---

### Post by superm1 on 2009-01-19
> **larainzlo07 said:**
> I am currently running Ubuntu 8.10 on my Dell Mini 9 and I am wondering if anyone has successfully mapped a key to turn on/off their bluetooth. I have the Airplane Mode program that lets you do this but I would prefer to not have to mess with that everytime to turn it on/off.
Airplane mode should already be mapped to one of the function keys if i'm not mistaken...

---

### Post by larainzlo07 on 2009-01-20
> **ajmorris said:**
> hi there,
this is very accomplishable. Assuming you have the x11-utils package installed (installed by default from a live/alternate cd install)
run:
```
xev
```



When i do that it just prints out a bunch of stuff to the screen it never displays a keycode after I do a combo of keys.

---

### Post by larainzlo07 on 2009-01-20
> **superm1 said:**
> Airplane mode should already be mapped to one of the function keys if i'm not mistaken...

Well thats the problem. The option is there under bluetooth for the dell power switch option but it is greyed out so if you click next to the check box nothing happens. I'll get you a screenshot ASAP to see what i am talking about.


EDIT*** Sorry for the delay i have attached the screenshot

---

