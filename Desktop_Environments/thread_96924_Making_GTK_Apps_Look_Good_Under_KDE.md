---
title: "Making GTK Apps Look Good Under KDE"
date: 2005-11-29
forum: Desktop Environments
---

### Post by jlacroix on 2005-11-29
Hello everyone, I have Ubuntu 5.10 installed however I also use KDE. I use both, actually, because I don't necessarily favor one over the other, which I am using (KDE or Gnome) basically depends on how I am feeling that particular week.

Anyway I installed a Virus through Synaptic (the virus is named something like "gtk-themes-qt" or something like that, an app thats supposed to make your GTK apps look like QT apps. It worked, while in KDE, but it makes Gnome look HORRIBLE when I log into Gnome and crashes things. (The Ubuntu team should remove this virus from its repository).

After removing that package, everything is back to normal but GTK apps still look ugly under KDE. Is there any other way to fix this?

Also since I removed the said package I am not sure if Gnome is still using Cairo now, like it used to, any way to check on that?

---

### Post by mcmuffy on 2005-11-29
Now I am not surre if you are joking (its almost 3am so I have an excuse) or english is not your 1st langauge and you are mixing what you think is a bugged (ie broken) app with a virused one.
If the latter then I have used the gtk-qt theme program before with no ill effects so you may need to be more specific about the error or what you are doing with the program.

---

### Post by jlacroix on 2005-11-30
If I turn on the KDE GTK thing, next time I log into Gnome, Gnome uses QT instead of GTK and looks wierd and ends up crashing. I say its a virus because it makes things crash and is really hard to remove.

---

### Post by Jessehk on 2005-11-30
[QUOTE=jlacroix]If I turn on the KDE GTK thing, next time I log into Gnome, Gnome uses QT instead of GTK and looks wierd and ends up crashing. I say its a virus because it makes things crash and is really hard to remove.[/QUOTE]


Then you would be wrong :)

Buggy software is not malicious software.

To remove it, simply type 

```


sudo apt-get remove packageName


```

replacing packageName with the name of the package

---

### Post by jlacroix on 2005-11-30
I know how to remove software. The package was removed but the damage remains after removing it.

---

