---
title: "why doesn't alt+kp enter open properties as alt+enter?"
date: 2015-12-02
forum: Desktop Environments
---

### Post by VitasLoWang on 2015-12-02
Hello, this might sound silly for some of you big linux geeks, but I really don't understand why nautilus or caja (these I tested) don't open folder properties upon pressing alt+small enter. It just goes into that folder like I did not hold that alt at all! Why does it force me to make those another 20cm hand movement from the mouse to the left to reach for the big enter? :) That's pretty user unfriendly IMHO. I am not sure if this happens in unity as well. I tested on Mate-desktop and also on Red Hat linux nautilus. How do I fix this drawback and is there any reason why this is not a default already?

---

### Post by ian-weisser on 2015-12-03
Unclear....

What is a 'small enter' ?
And why would it have identical keymappings to 'big enter'?

---

### Post by grahammechanical on 2015-12-03
It is the difference in results between Alt+Enter (main section of the keyboard) = opens the properties dialog of whatever folder has been selected, and Alt+Enter (numerical keypad section of the keyboard) = opens the folder.

It seems that when using the Alt+Enter combination on the numerical keypad that the press of the Alt key is ignored & Nautilus responds as if only an Enter key had been pressed. And the reason for this behaviour? No idea.

Regards.

---

### Post by VitasLoWang on 2015-12-03
If somebody had an idea how to "fix" this and configure this keyboard shortcut to save me from moving my hand too far that would be cool :) But I am not sure if this is possible without recompiling...
You know I was not really surprised when I found out that alt and altGr behave differently, but in case of enters I am :-]

---

### Post by CantankRus on 2015-12-03
In nautilus try setting the accelerator in **~/.config/nautilus/accels**

Kill nautilus...
```
nautilus -q
```
Open **~/.config/nautilus/accels** in your text editor and
search for "DirViewActions/Properties" and change the accelerator to "**<Alt>KP_Enter**" and remove the semi-colon "**;**" at the start of the line.
The line should now look like...
```
(gtk_accel_path "<Actions>/DirViewActions/Properties" "<Alt>KP_Enter")
```

---

### Post by VitasLoWang on 2015-12-03
thanks CantankRus but this makes alt+enter stop working the same way as alt+kp_enter did before :-] The malfunction only changes but still remains present. I guess I cannot set more keys to this [COLOR=#000000][FONT=Ubuntu Mono]<Actions>/DirViewActions/Properties" can I?[/FONT][/COLOR]

---

### Post by CantankRus on 2015-12-03
Try mapping kp_enter to the Return key.

Kill nautilus..
```
nautilus -q
```

Change the line in  ~/.config/nautilus/accels back to...
```
; (gtk_accel_path "<Actions>/DirViewActions/Properties" "<Alt>Return")
```

Check your keycode for kp_enter by running the following xev command then hit your keypad Enter key.
```
xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'
```

Then in the terminal run...
```
xmodmap -e 'keycode [COLOR="#FF0000"]104[/COLOR]=Return'
```
using [COLOR="#FF0000"]your keycode[/COLOR].

Running the previous xev command should now show "Return" when you hit the Enter and  KP_Enter keys.
eg
```
**[COLOR="#006400"]glen@Trusty:~$[/COLOR] xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'**
36 Return
104 Return
```

Add the command...
```
xmodmap -e 'keycode [COLOR="#FF0000"]104[/COLOR]=Return'
```
to startups.

---

