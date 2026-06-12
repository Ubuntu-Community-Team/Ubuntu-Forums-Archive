---
title: "Windows title bar turn brown after restart???Had MacOSX Theme running"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by boeing777 on 2007-10-31
Hi, I have MacOsX Transformation pack installed, everything was working perfectly, the  bar was good.  However, when i restarted my computer, the title bar becomes brown and all the button went back to the right side.  Attachment below is a picture of what my current problem look like, it used to look like MAC window before the restart

---

### Post by Zorael on 2007-10-31
I'm not sure I follow you, but have you tried launching emerald-theme-manager and reselecting your MacOSX theme?

---

### Post by boeing777 on 2007-10-31
what happen was when i installed the mac osx transformation pack, everything looks good including the title bar with buttons on the right like in Mac.  When i restarted my computer, the title bar no longer fit my theme, it changed to brown

---

### Post by boeing777 on 2007-10-31
so now the problem is that no matter which theme i choose, the title bar looks the same, it does not change.

---

### Post by Zorael on 2007-10-31
I don't see the brown in your screenshot, but I'm going to assume you mean the Human theme that's the standard one in Ubuntu.

Is both Compiz and Emerald running?

```
$ compiz --replace
```

It should start Emerald automatically, if you have the Window Decoration plugin enabled.

Else, run:
```
$ emerald --replace
```

---

### Post by boeing777 on 2007-10-31
Hi,Thank you so much for your help.  

The problem now is that when i turned the effect off, the mac theme title bar shows properly, i typed compiz--replace, the title bar is gone now.

---

### Post by Zorael on 2007-10-31
Er, turned the effect off? I don't quite follow, so bear with me if I run off in the wrong direction.

Basically, with Compiz running, you need to get a window decorator running to get title bars. This can be metacity, kde-window-decorator, and/or emerald. There's probably some more I don't know about.

If you don't have the Window Decoration plugin enabled, you need to launch one manually. Window Decoration does this for you. Just make sure the Command field has 'emerald --replace' as its value, if you want to use Emerald.

If you don't have it enabled, you need to start it yourself.

---

### Post by boeing777 on 2007-10-31
i fix with by replacing emerald with window decorator? i know what my problem was now at the beginning, i installed emerald and then restart the computer, and the title bar just changed. was that the problem maybe?

---

### Post by Zorael on 2007-10-31
Emerald *is* a window decorator.

Chances are you need it running to see your MacOSX theme. If your theme is brown, that suggests you haven't started it yet.

Just copy/paste this command into a terminal and see if it helps:
```
compiz --replace & emerald --replace &
```

---

### Post by boeing777 on 2007-10-31
the theme was perfect without emerald, until i installed emerald and restarted my computer, the title bar changed.  so i replaced emerald and uninstalled it.

---

