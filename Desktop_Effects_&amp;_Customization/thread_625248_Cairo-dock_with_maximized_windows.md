---
title: "Cairo-dock with maximized windows"
date: 2007-11-27
forum: Desktop Effects &amp; Customization
---

### Post by krazedkid on 2007-11-27
Is it possible to make it so Cairo-Dock doesn't overlap the maximized window, but makes it maximize to the edge of the dock? like in OS X?

---

### Post by sztomi on 2008-02-26
Yes!

You will need to edit cairo-dock.conf, which can be found in [FONT="Courier New"]~/.cairo-dock/current_theme/cairo-dock.conf[/FONT]

The following lines should be somewhere at 37th line:

```
[FONT="Courier New"]#b- Reserve space at the edge of the screen for the dock ?
#{This will prevent other windows from overlapping the dock.}
reserve space=*false*[/FONT]
```

All you have to do is simply replace the *false* with *true.* I wonder why they didn't put this on the GUI, it's a quite common feature IMHO. Maybe in later versions.

:guitar:

(I just love this smiley :D)

---

### Post by coolfire92 on 2008-07-07
Hey cool. But where is this file?
~/.cairo-dock/current_theme/cairo-dock.conf

How do I navigate to ~/.cairo-dock? Which folder is it in?

Sorry for asking such a lame question. I'm very very new to ubnutu :)

Using Hardy Heron. is it the same as mentioned in this post?

Thanks in advance! :)

---

### Post by sztomi on 2008-07-07
Hi!

~ refers to your home directory, which is precisely **/home/*yourname***, obviously yourname being your login name in ubuntu. (it doesn't matter which version you are using for this one - this is standard).

To navigate to that folder either you need to enable showing "hidden" files in your graphical sheel (possibly it's Nautilus) OR you need to use Midnight Commander (mc) OR use command line. 

To install mc type: 
```
sudo apt-get install mc
```
in the command line. When finished, you start it simply typing mc. It is very easy to use and if you are familiar with two-panel filemanagers, it will be one of your favourite tools. When you navigate to the desired file, hit F4 to use mc's built in text editor. 

To do it all in commandline:
```

cd ~/.cairo-dock/current_theme
gedit ./cairo-dock.conf

```

*(see? this one is nearly always the fastest)* ;)

You can replace gedit with your favourite text editor.

Have fun!

:guitar:

---

### Post by fabounet on 2008-07-08
please don't use such a hack ! 
right click -> Cairo-Dock -> configuration, tick the corresponding box in the first tab.

---

### Post by sztomi on 2008-07-08
Well, that's it. When I used cairo-dock, this feature wasn't exposed on the UI.

---

### Post by fabounet on 2008-07-09
really weird, which version do you use ?
it should appear in the config panel so check it before editing the .conf file.

---

### Post by sztomi on 2008-07-09
I said when I use**d** it. I don't know which version was it, but I'm sure I checked the GUI first and then needed to search google for a solution.
:guitar:

---

### Post by fabounet on 2008-07-10
ok, so I don't think one can have this problem anymore ;-)

---

