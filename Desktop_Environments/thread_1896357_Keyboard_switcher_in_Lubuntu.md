---
title: "Keyboard switcher in Lubuntu?"
date: 2011-12-16
forum: Desktop Environments
---

### Post by M_Mynaardt on 2011-12-16
Hi!

I recently installed Lubuntu on my laptop.  It's working well enough.  But one thing I do like is being able to switch keyboard layouts on occasion.  That's easy enough with an applet in Xfce or GNOME.  But I've not figured out how to do so in LXDE.

Does anyone know of a keyboard switcher, or method, in LXDE or Lubuntu?

Thanks...

---

### Post by Rex Bouwense on 2011-12-16
With a quick google search I found this:
[http://ubuntuforums.org/showthread.php?t=1455877](http://ubuntuforums.org/showthread.php?t=1455877)
If you read the whole post you will find a possible solution (post #8 specifically).  I haven't tried it but someone did and it worked for him.

---

### Post by M_Mynaardt on 2011-12-23
> **Rex Bouwense said:**
> With a quick google search I found this:
[http://ubuntuforums.org/showthread.php?t=1455877](http://ubuntuforums.org/showthread.php?t=1455877)
If you read the whole post you will find a possible solution (post #8 specifically).  I haven't tried it but someone did and it worked for him.

Okay, I'm **ALMOST** there!

I figured out I could do the following:
```
:~$ setxkbmap -layout "us,gr,es,epo" -option "grp:alt_shift_toggle"
```

That gave me the US, Modern Greek, Spanish and Esperanto keyboards to switch between.

**However**, I'm a bit fussy...

Instead of "us" I would like something that's for "Canada English" keyboard.  I know it's exactly the same as the American keyboard layout, but I want a Canadian flag on the Keyboard Layout Switcher applet on the panel, not the American flag.

I tried messing about with "ca en" or "ca english" instead of "us", but no joy..  :(

The other thing I need is the _Polytonic_ Greek (i.e. Ancient Greek, with the zillions of accent marks), not the modern Greek.  I did try "gr polytonic" but that didn't help either.

If anyone could tell me those two layout codes (Canadian English keyboard for the flag thing and Polytonic Greek for ancient Greek accents), then I'll be a happy camper!  :)

And now that my little grey cells are kind of sparking, a bit, does anyone know of a keyboard layout you can choose for Old English?  Just so you can type the letters "eth" and "thorn".  Maybe the Icelandic keyboard?  Which I'm guessing would be "is" layout code.

Thanks in advance!

---

### Post by GeorgeVita on 2012-01-15
> **M_Mynaardt said:**
> ...I figured out I could do the following:
```
:~$ setxkbmap -layout "us,gr,es,epo" -option "grp:alt_shift_toggle"
```
That gave me the US, Modern Greek, Spanish and Esperanto keyboards to switch between.Instead of "us" I would like something that's for "Canada English" keyboard.  I know it's exactly the same as the American keyboard layout, 

**However**, I'm a bit fussy...
... but I want a Canadian flag on the Keyboard Layout Switcher applet ...

The other thing I need is the _Polytonic_ Greek (i.e. Ancient Greek, with the zillions of accent marks), not the modern Greek...

Using the terminal command "setxkbmap" you can test the result but the solution is not permanent. Some ideas to test:

Check current xkb parameters with: ```
setxkbmap -query
```
Set us,ca,gr layout with variants default (us), eng (ca) and polytonic (gr) that can be changed with ALT-SHIFT keys:
```
setxkbmap -layout "us,ca,gr" -variant ",eng,polytonic" -option "grp:alt_shift_toggle"
```

Test if all are OK and make all changes permanent:
```
gksudo leafpad /etc/default/keyboard
```

Change parameters to the following:
```
XKBMODEL="pc105"
XKBLAYOUT="us,ca,gr"
XKBVARIANT=",eng,polytonic"
XKBOPTIONS="grp:alt_shift_toggle"
```

Save, exit, reboot.

Note that XKBMODEL="pc105" fits to my keyboard, you may use your existing code.

More info from terminal:
```
man setxkbmap
cat /usr/share/X11/xkb/rules/evdev.lst
```

G

---

### Post by M_Mynaardt on 2012-01-15
> **GeorgeVita said:**
> Using the terminal command "setxkbmap" you can test the result but the solution is not permanent. Some ideas to test:

Check current xkb parameters with: ```
setxkbmap -query
```
Set us,ca,gr layout with variants default (us), eng (ca) and polytonic (gr) that can be changed with ALT-SHIFT keys:
```
setxkbmap -layout "us,ca,gr" -variant ",eng,polytonic" -option "grp:alt_shift_toggle"
```

Test if all are OK and make all changes permanent:
```
gksudo leafpad /etc/default/keyboard
```

Change parameters to the following:
```
XKBMODEL="pc105"
XKBLAYOUT="us,ca,gr"
XKBVARIANT=",eng,polytonic"
XKBOPTIONS="grp:alt_shift_toggle"
```

Save, exit, reboot.

Note that XKBMODEL="pc105" fits to my keyboard, you may use your existing code.

More info from terminal:
```
man setxkbmap
cat /usr/share/X11/xkb/rules/evdev.lst
```

G

Thank you so much for that!  Now it works just fine!  For some reason, if I use **setxkbmap** for multiple keyboard layouts, it does not cycle through them in the order I expected.  If I have 4 keyboards listed, the toggle cycles through them not 1,2,3,4, but 1,4,3,2.  At least now I know how to switch the keyboard layouts to something I can use on occasion.

With your help, using this code:
```
:~$ setxkbmap -layout "ca,gr,epo,es" -variant "eng,polytonic, ," -option "grp:alt_shift_toggle"
```

So, that way I can cycle through they keyboards in the following order: Canadian English, Spanish, Esperanto, and Polytonic Greek.

And the keyboard switcher changes the flag graphics just the way I want it to!

Very cool indeed!

Thanks again for that!  Never would've figured that out on my own (working nights is my excuse)...
\\:D/,eng,polytonic

---

