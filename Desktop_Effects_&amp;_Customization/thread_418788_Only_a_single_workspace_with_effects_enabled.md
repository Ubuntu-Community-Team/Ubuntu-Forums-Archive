---
title: "Only a single workspace with effects enabled?"
date: 2007-04-22
forum: Desktop Effects &amp; Customization
---

### Post by Mr Sprout on 2007-04-22
I've enabled the Fiesty desktop effects, including the 'workspaces on a cube'. However, when I try to rotate the cube using Ctrl + Alt + Drag nothing happens. 

I'm thinking that perhaps I only have one workspace enabled because I cant see why it's not rotating. How do I add more workspaces, I've tried adding them from the workspace toolbar with no luck.

Thanks!

---

### Post by MRiGnS on 2007-04-22
run gconf-editor.

apps --> compiz --> general --> screen0 --> options and change hsize to you flavour.

---

### Post by Mr Sprout on 2007-04-22
> **MRiGnS said:**
> run gconf-editor.

apps --> compiz --> general --> screen0 --> options and change hsize to you flavour.

You rock, thanks so much.

You probably wouldn't believe I had actually searched for some time before coming here to ask. Sorry if I've wasted your time.

---

### Post by MRiGnS on 2007-04-22
> **Mr Sprout said:**
> You rock, thanks so much.

You probably wouldn't believe I had actually searched for some time before coming here to ask. Sorry if I've wasted your time.

np.

u could have also used gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4

forgot that one :>

---

### Post by dracule on 2007-04-22
i have a very similar problem

i enabled desktop effects. everything was working good, i could move the cube around and everything. now i cant get the cube to work. when i do ctrl+alt+left or right, nothing happens. before it would rotate the cube. i did what you mentioned in the post and for number of desktops it says 4. all the wiggly effects still work.

---

### Post by MRiGnS on 2007-04-22
is the cube activated in the desktop-effects menu?

run gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1

try if alt+ctrl+mouse_button_1 works to rotate the cube.

oh, and are there actually more than one dekstop shown on the pager?

---

### Post by dracule on 2007-04-22
yes, it is enabled. it just all of the sudden stopped when i started watching a movie. 

what you gave me still didnt work.

---

### Post by MRiGnS on 2007-04-22
i'm kind of clueless about this one. i need more input.

try using this script:

```
 gksudo gedit (or kdesu kate if using kde) /usr/local/bin/compiz-reset 
```

now copy and paste:
```
killall -9 compiz.real
compiz --replace
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1

```

save the file

```
sudo chmod -x /usr/local/bin/compiz-reset && sudo chmod 667 /usr/local/bin/compiz-reset
```

close the terminal.

hit alt+f2 and type compiz-reset

---

### Post by dracule on 2007-04-22
it worked!!!! thank you! now if it didnt kill my sound :(


EDIT sound problem gone, i think i messed it up by hibernating in windows.

---

### Post by mgmiller on 2007-04-22
There is a nice GUI for all this stuff:
```
apt-get install gnome-compiz-manager
```
It is in the universe repository, so enable that first if need be.

Then look in your System>Preferences> GL Desktop.

It has a nice tray icon to turn compiz on and off and many setting for cube and other effects.  Much easier than gconf editor.

---

