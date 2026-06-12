---
title: "Ubuntu Skins?"
date: 2007-11-03
forum: Desktop Effects &amp; Customization
---

### Post by Lopas1 on 2007-11-03
How to i install skins/themes like this one?
[http://www.gnome-look.org/content/show.php/Aqua+Button+Look?content=66690&PHPSESSID=af7daeeaa93c3d26d6039a5c3a000bd1](http://www.gnome-look.org/content/show.php/Aqua+Button+Look?content=66690&PHPSESSID=af7daeeaa93c3d26d6039a5c3a000bd1)


??
Do i need something extra than ubuntu?
I dont know what i got since i installed ubuntu 7.10 thru wubi and is compleeeeeetely noob...
I know i got the cube and some effects :D 
I think i got compiz since i got the compizconfig settings manager!

Help me! i wanna have a sexy skin!  :lolflag:

---

### Post by ecschiel on 2007-11-03
For using that theme you need emerald.
```
sudo apt-get install emerald
```
or using Synaptic otherwise (If you don't have already installed)

Once you get that installed just download the theme and import it with the emerald theme manager (type emerald-theme-manager in a console or go to System->Preferences->Emerald Theme Manager)

---

### Post by SomeGuyDude on 2007-11-03
What after that? I have my emerald manager open, imported the theme, but nothing's changed. There's no "apply theme" button or anything.

---

### Post by EtrnlApocaplypse on 2007-11-03
> **SomeGuyDude said:**
> What after that? I have my emerald manager open, imported the theme, but nothing's changed. There's no "apply theme" button or anything.

you have to start emerald!

---

### Post by Zorael on 2007-11-03
The Emerald manager will only apply a chosen theme if you first make Emerald *replace* your current window decorator. I don't believe there is a shortcut for this, but you can make a launcher, type it in a run box, or execute it from a terminal.

```
emerald --replace
```

(If you run it from a terminal, don't forget to add an ampersand **&** to the end to "keep control" of the terminal session.)

---

### Post by SomeGuyDude on 2007-11-03
> **EtrnlApocaplypse said:**
> you have to start emerald!

All I did was the "sudo apt-get install emerald" command in terminal, then I opened up the manager. Was I supposed to do something else?

As a side note, diving into eye candy my first whack at Ubuntu seems to work well. Even if I screw something up, it's nothing crucial.

---

### Post by Zorael on 2007-11-03
> **SomeGuyDude said:**
> As a side note, diving into eye candy my first whack at Ubuntu seems to work well. Even if I screw something up, it's nothing crucial.

"To screw up Windows, you just need to work on it. To screw up Linux, you need to work at it."

---

### Post by SomeGuyDude on 2007-11-03
> **Zorael said:**
> The Emerald manager will only apply a chosen theme if you first make Emerald *replace* your current window decorator. I don't believe there is a shortcut for this, but you can make a launcher, type it in a run box, or execute it from a terminal.

```
emerald --replace
```

(If you run it from a terminal, **don't forget to add an ampersand [b]&** to the end to "keep control" of the terminal session[/B].)

I'm afraid I don't know what this part means. So would I put in "emerald --replace&" ?

Sorry to hijack the thread, but I have a feeling it's still on the subject of getting that nifty theme to work.

EDIT: Okay, I did that. But... something went awry. If I close my terminal window, the toolbars vanish and everything goes kerflooey. This happens with or without the &.

---

### Post by Zorael on 2007-11-03
The ampersand is there to prevent that from happening. :> I'm not sure what happened if it didn't.

Anyway, hit Alt+F2. That should spawn a run box. Enter 'emerald --replace' there, and you should get it running.

---

### Post by pjones0404 on 2007-11-03
another easy way to do this is to install emerald and import the theme and all. 

then go to the compiz settings manager and select windows decorations. in the command field just type in the word emerald. 


then log out and back in and it should load the emerald windows decorations.

---

### Post by SomeGuyDude on 2007-11-03
> **Zorael said:**
> The ampersand is there to prevent that from happening. :> I'm not sure what happened if it didn't.

Anyway, hit Alt+F2. That should spawn a run box. Enter 'emerald --replace' there, and you should get it running.

THERE we go. Thank ya.This emerald thing is nifty. So many wacky animations with this + compiz + AWN.

---

