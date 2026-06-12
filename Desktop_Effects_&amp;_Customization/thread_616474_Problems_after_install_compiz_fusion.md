---
title: "Problems after install compiz fusion"
date: 2007-11-18
forum: Desktop Effects &amp; Customization
---

### Post by louvros10 on 2007-11-18
After installing compiz fusion and give in the terminal: $ sudo apt-get install xserver-xgl to make compiz running, I have 2 problems.
1)I can't switch to greek layout of the keboard
2)Display sleeps when I watch a movie after 10 minutes.
Any help???
I won't play again with compiz fusion!!!:mad::mad::mad:
Tired losing my time just to work things out...:(:(:(

---

### Post by chrome101 on 2007-11-18
I have similar problems with compiz:
 1. Screensaver cuts in after 10mins when watching movies... Tried to change with no effect.
 2. When changing movie size or closing media player... it hangs.
 3. When trying to watch streams (BBC Click for example)... Computer reboots!

Was first impressed with compiz 3d cube thingy, but as I need my laptop for media stuff, I would advice not to use at all.

---

### Post by chrome101 on 2007-11-18
Just disabled compiz and everything works properly and no crashes... 

Systems > Preferences > Appearances >Visual Effects

Select the 'None'. 

There... no more problems!

---

### Post by louvros10 on 2007-11-18
What about the keyboard layout switching into an other languege???:confused:

---

### Post by chrome101 on 2007-11-18
Mine changed from UK to USA... Changed it back

Try this:

Right click on the Main menu

Select: + Add to Panel
Scroll down to 'Utilities' section 
Select: Keyboard Indicator

This should show the current country layout.

Right click on the layout menu > keyboard preferences > Layout
Click 'Choose'

Select your countries layout from list and > OK
It should appear in the list select this and close


You should now be able to change keyboard layout if it changes again without problems

Goodluck

---

### Post by Ub1476 on 2007-11-18
Hardware?

---

### Post by xAEE on 2007-11-18
Well, I can help with the second problem...change the idle settings or have a look at them.

---

### Post by chrome101 on 2007-11-18
Doesn't work... I changed it to maximum and screen keeps going blank after 10mins. Not a biggy for me though.

---

### Post by Forlong on 2007-11-18
Try adding this to the xorg.conf:

```
Section "Serverflags"
Option "NoPM" "True"
EndSection
```

---

### Post by chrome101 on 2007-11-18
Xaee... 
Done that... I'll sort it when I got time...

---

