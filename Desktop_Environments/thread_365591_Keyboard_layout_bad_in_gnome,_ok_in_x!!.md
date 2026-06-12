---
title: "Keyboard layout bad in gnome, ok in x!!"
date: 2007-02-19
forum: Desktop Environments
---

### Post by solanas53 on 2007-02-19
I have Ubuntu 6.06 installed on a Compaq notebook 100.
When i run recovery mode or whenever gnome is not running, the keyboard works fine.
But when running gnome, whether I use a virtual terminal or some text editor, the keyboard behaves as if de fn key was pressed all the time!!!!!!!!!!!
I can't write because letters become numbers!

I ran dpkg-reconfigure xserver-xorg and changed things there, and when gnome starts up, it asks whether i'd like to keep my x settings or my gnome settings. Whatever I say it doesn't work.

I'd like to keep my x settings, without letting gnome's configuration interfere.

Any help?

Thanks in advance

---

### Post by ubix on 2007-02-19
In Ubuntu 6.10 you can manage keyboards via **[COLOR="Blue"]System -> Preferences Keyboard[/COLOR]**. There you select the **[COLOR="Blue"]Layout tab[/COLOR]**, where you can add different keyboard styles. If you do not want to have a multilingual system there should be only one keyboard layout set (you can remove what you don't need).

If you want to use multilingual system with more keyboard layouts install a keyboard indicator, by R-clicking on the panel and select **[COLOR="Blue"]+ Add to Pane[/COLOR]l**, find the item called **[COLOR="Blue"]Keyboard Indicator[/COLOR]**, and hit the **[COLOR="Blue"]+ Add[/COLOR]** button.

You can control which keyboard should be active via this **[COLOR="Blue"]Keyboard Indicator[/COLOR]**. Make sure the right language is set (some applications may remember the last use, so whenever you start an editor, check the above language/keyboard [COLOR="Blue"]indicator).[/COLOR]

---

### Post by solanas53 on 2007-02-19
Thanks for responding.

I can find the correct layout for me, but I have to keep the fn key pressed to write correctly (right now, for example).
None of the layouts shown will make that change.

How can I keep the primitive keyboard configuration that works ok in the recovery mode?

Thank you!

---

### Post by guysmiley25 on 2007-02-20
I am having the same problem, right now i'm holding down the fn key to type.

i'm running xubuntu edgy. i did not have this problem in xubuntu dapper.

i also have tried dpkg-reconfigure with no luck.

anyone please help as this is very annoying.

---

### Post by ubix on 2007-02-20
Ooops, I realized I again got it all wrong. I missed the FN. This problem is beyond me! :(

---

### Post by guysmiley25 on 2007-02-21
Bump!

---

### Post by solanas53 on 2007-02-21
num-lock was on.. that hurts

---

### Post by guysmiley25 on 2007-02-22
Thanks heaps! but that is going to happen every time the GUI starts! any ideas on how to stop it?

---

### Post by guysmiley25 on 2007-02-28
Here is my solution.

I'm running xubuntu edgy eft, However you could make it work with others.

First install numlockx if you do not already have it:
```
sudo aptitude install numlockx
```

Now in my case I would go:
```
sudo mousepad /usr/share/xsessions/xfce4.desktop
```

Comment out the line that has "Exec=startxfce4" and add the line "Exec=/usr/local/bin/xfce4.sh"
```

...
#Exec=startxfce4
Exec=/usr/local/bin/xfce4.sh
...

```

Now go
```
sudo mousepad /usr/local/bin/xfce4.sh
```

and enter
```

#!/bin/bash
numlockx off
startxfce4
exit

```

Finally
```
sudo chmod +x /usr/local/bin/xfce4.sh
```

Hope that helps.

---

