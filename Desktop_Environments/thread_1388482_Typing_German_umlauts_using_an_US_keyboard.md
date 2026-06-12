---
title: "Typing German umlauts using an US keyboard"
date: 2010-01-23
forum: Desktop Environments
---

### Post by f.zweig on 2010-01-23
Hello there!

I'm having a little problem with my keyboard layout settings on Ubuntu Karmic. Using an US layout, I was able to print German umlauts (mutated vowels) using the right CTRL key plus one of the keys ";", "'" and "[" (keycodes 47, 48 and 34). But this was only possible in gnome-terminal and the ttys, all the other apps just printed the American characters. After playing with my keyboard layout settings a bit (having no luck and restoring them to defaults using the button in gnome-keyboard-properties), I lost this configurations and am not able to print umlauts any more. 

After generating a .Xmodmap file using
```
xmodmap -pke > .Xmodmap
```I discovered that there are entries for the characters [aouAOU]diaeresis (representing the umlauts) for these keycodes. So, the problem is that GNOME doesn't respect these settings, but uses it's own layout instead.

I recently found a bug for xkb-data ([https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/408397](https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/408397)) which may be or may not be adhere to this behaviour, however, installing the patched package from comment #6 doesn't help anything.

Testing Ubuntu Lucid, I was not able to reproduce the wanted behaviour.

So, finally my question is: How can I make GNOME respect the settings from the default /usr/share/xmodmap/xmodmap.xy and get the desired behaviour back and use it system-wide, not only in gnome-terminal and TTYs?

I'm looking forward to any help and will be glad to answer any further questions! :-)

Regards,
Felix

p.s.: For anyone speaking German, I also wrote a post in the German forum, but didn't got a reply there. Have a look at [http://forum.ubuntuusers.de/topic/umlaute-auf-us-tastatur/](http://forum.ubuntuusers.de/topic/umlaute-auf-us-tastatur/) for more detail.

---

### Post by Lizzy on 2010-01-24
realy weird :D, i'm using a norwegian keyboard but i don't have to use the CTRL button to write umlaute in german... i just press '' followed by a e o u ------ which results in ö ü ä , Ä Ü Ö .

---

### Post by Leppie on 2010-01-24
i believe the keyboard layouts with dead keys have to be selected to be able to use " as the umlaut.

---

