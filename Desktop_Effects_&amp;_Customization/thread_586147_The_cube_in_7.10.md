---
title: "The cube in 7.10"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by Dapman01 on 2007-10-22
Is the 3d cube available in gusty?
if so how do I find it
I got the drivers installed

---

### Post by Caffeine_Junky on 2007-10-22
Install this, ..either from Synaptic Package Manager or from Terminal:

```
 sudo apt-get install compizconfig-settings-manager
```

...then look for the effects controls under: 
System >  Preferences > Appearance > Visual Effects.
  
and:
System > Preferences > Advanced Desktop Effects Settings

---

### Post by IWood on 2007-10-22
So...if I've got the Advanced Desktop Settings tool installed, and "Desktop Cube" checked off, what else do I need to be checking if I still can't get the cube?

(N00b sez what?)

---

### Post by Dapman01 on 2007-10-22
> **Caffeine_Junky said:**
> Install this, ..either from Synaptic Package Manager or from Terminal:

```
 sudo apt-get install compizconfig-settings-manager
```

...then look for the effects controls under: 
System >  Preferences > Appearance > Visual Effects.
  
and:
System > Preferences > Advanced Desktop Effects Settings

worked perfect, thanks
Do you know to to make it so that when I exit a window, fire burns from the bottom of the window up

---

### Post by XNYE on 2007-10-22
When I type the sudu apt-get install... command in the terminal I get "Couldn't find package compizconfig-settings-manager"

Also, where can I find all the hot keys?  I've spent an hour googling and can't find any documentation on them.  ig. scaling, expo effects

thanks

---

### Post by Soarer on 2007-10-22
> **XNYE said:**
> When I type the sudu apt-get install... command in the terminal I get "Couldn't find package compizconfig-settings-manager"

Also, where can I find all the hot keys?  I've spent an hour googling and can't find any documentation on them.  ig. scaling, expo effects

thanks

It's in the 'Universe' repository. Make sure you have that enabled and 'reload'.

Can't help with the 2nd Q, sorry.

---

### Post by XNYE on 2007-10-22
> **Soarer said:**
> It's in the 'Universe' repository. Make sure you have that enabled and 'reload'.

Can't help with the 2nd Q, sorry.


I have no idea what the 'Universe' repository is but in my lost attempt to get things working I tried that sudo -apt-get command in the above post and it worked this time... for some reason.  Now to see if I can complete the steps.

Thanks

---

### Post by XNYE on 2007-10-22
Great... it all worked.  One question though, how do I know what key commands will do the specific effect?  Like the cube?  Or the widget layer? Or desktop pane?

Thanks

---

### Post by z0phi3l on 2007-10-22
> **XNYE said:**
> Great... it all worked.  One question though, how do I know what key commands will do the specific effect?  Like the cube?  Or the widget layer? Or desktop pane?

Thanks

Should be in the Actions tab of each pluging.

I think by default the Cube is Click+hold muse wheel

---

### Post by XNYE on 2007-10-22
[QUOTE=z0phi3l;3602548]Should be in the Actions tab of each pluging.

I think by default the Cube is Click+hold muse wheel[/QUOTE

Thanks... the Actions tab is where it's at... I just didn't realize that I had to expand it. (UGH... again with the random key strokes on firefox..(firefox is all I've used at this point)  It just randomly focuses somewhere else in the window so I have to use my mouse to put the curse back at this sentence) If anyone knows how to fix this that is look at this thread, let me know.  ( I know it's off topic )

How did you know by default that I could use Click+Hold mouse wheel? I didn't see that in the actions tab.

Thanks.

---

### Post by TadH on 2007-10-22
here are some shortcuts

ctrl+alt+d fade all windows to desktop
alt+scroll make ur winow transparent
winkey+tab the itunes thing

---

### Post by XNYE on 2007-10-22
> **TadH said:**
> here are some shortcuts

ctrl+alt+d fade all windows to desktop
alt+scroll make ur winow transparent
winkey+tab the itunes thing

Thank you!  These are the kind of shortcut keys I've been looking for.  

I had made a window transparent but had no idea how... I wasn't even touching the mouse when it happened... Linux for some reason does random things. ig. goes off focus, switches windows, moves up 4 lines.

ARG, it just happend.

Thanks and if anyone as more, please let me know..

so far I know
> Ctrl+Alt+(left or right arrow)
Shift+alt+Uparrow
Crtl+Alt+DownArrow
of course Alt+Tab
Ctrl+Alt+Shift+(Left or Right arrow) to move current window to other workspace
Ctrl+Alt+LeftMouse button
Click Middle Mouse Button to move cube
Super+E


---

### Post by AlienTech on 2007-10-25
(SOLVED) So I really want fusion like I had with 7.04 but here's what I get.....


paul@Alien:~$  sudo apt-get install compizconfig-settings-manager
[sudo] password for paul:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  python-compizconfig
The following NEW packages will be installed:
  compizconfig-settings-manager python-compizconfig
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/547kB of archives.
After unpacking 3506kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/available' near line 2 package `linux-libc-dev':
 value for `status' field not allowed in this context
E: Sub-process /usr/bin/dpkg returned an error code (2)
paul@Alien:~$ 


OK... any ideas? I'm still pretty knew and have no clue. TY in advance


Found my own answer: sudo dpkg --clear-avail && sudo apt-get update

to anyone else having this issue:

---

