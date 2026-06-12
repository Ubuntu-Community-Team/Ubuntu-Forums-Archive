---
title: "'Decoration windows' rule does not properly update with Emerald"
date: 2011-03-25
forum: Desktop Environments
---

### Post by WeltEnSTurm on 2011-03-25
I am using the Emerald window decorator and want to hide the titlebar of windows that are maximized.
In CompizConfig is an option for choosing which windows should be decorated, and since I don't want to decorate maximized windows, I added !state=maxvert.
This works well with the default GTK window decorator, but when using Emerald it fails:
first it seems working, but after unmaximizing a window suddenly all windows lack decoration.
It even stays that way when I readd 'any' to the line, I have to switch to the default decorator or restart gnome.
Now is there any way to make this work with Emerald? I would really like to keep my current theme while hiding full-screen title bars.

**Edit:**

Not exactly related:
I am also using Global Menu which is nice, but the window management menu (maximize, minimize, resize etc.) only works if the window list is activated too. Is there a solution or do I have to create a bug report at that project? :v

---

### Post by Krytarik on 2011-03-25
> **WeltEnSTurm said:**
> I am using the Emerald window decorator and want to hide the titlebar of windows that are maximized.
In CompizConfig is an option for choosing which windows should be decorated, and since I don't want to decorate maximized windows, I added !state=maxvert.
This works well with the default GTK window decorator, but when using Emerald it fails:
first it seems working, but after unmaximizing a window suddenly all windows lack decoration.
It even stays that way when I readd 'any' to the line, I have to switch to the default decorator or restart gnome.
Now is there any way to make this work with Emerald? I would really like to keep my current theme while hiding full-screen title bars.

Although Emerald is generally not *that* stable, e.g. when switching between its themes, I can't reproduce the described behaviour at my system, it works as expected.

However, I recommend using another window match, to really match only fully maximized windows:
```
!(state=maxhorz & state=maxvert)
```> **WeltEnSTurm said:**
> 
I am also using Global Menu which is nice, but the window management menu (maximize, minimize, resize etc.) only works if the window list is activated too. Is there a solution or do I have to create a bug report at that project? :v
Does it still work when you set "Skip taskbar" of Compiz' "Window Rules" plugin to "any"? I'm afraid it doesn't.

---

### Post by WeltEnSTurm on 2011-03-26
> **Krytarik said:**
> Howerver, I recommend using another window match, to really match only fully maximized windows:
```
!(state=maxhorz & state=maxvert)
```

I already tried that too, it doesn't keep my decorations from vanishing though. Still thank you.

> **Krytarik said:**
> Does it still work when you set "Skip taskbar" of Compiz' "Window Rules" plugin to "any"? I'm afraid it doesn't.

This keeps all windows from being shown in task bars/similar stuff, while not solving this issue. :p
I can live with clicking twice instead of once, I guess.

---

### Post by Krytarik on 2011-03-26
> **WeltEnSTurm said:**
> I already tried that too, it doesn't keep my decorations from vanishing though. Still thank you.
You may try upgrading Compiz through its own PPA, maybe it affects the handling of Emerald positively:
[https://launchpad.net/~compiz/+archive/ppa]("https://launchpad.net/%7Ecompiz/+archive/ppa")

Btw., what version of Ubuntu do you run?
> **WeltEnSTurm said:**
> This keeps all windows from being shown in task bars/similar stuff, while not solving this issue. :razz:
Ok, I didn't mind that any other "task manager" would also be affected. :P
What is actually the answer to my question, just curious?
> **WeltEnSTurm said:**
> I can live with clicking twice instead of once, I guess.
I don't really get this!?

---

### Post by WeltEnSTurm on 2011-03-26
> **Krytarik said:**
> You may try upgrading Compiz through its own PPA, maybe it affects the handling of Emerald positively:
[https://launchpad.net/~compiz/+archive/ppa]("https://launchpad.net/%7Ecompiz/+archive/ppa")

I'll try that.

> **Krytarik said:**
> Btw., what version of Ubuntu do you run?

Linux Mint 10 :'x

> **Krytarik said:**
> Ok, I didn't mind that any other "task manager" would also be affected. :P
What is actually the answer to my question, just curious?

I don't really get this!?

I want
[img]http://dl.dropbox.com/u/23989104/lookslike.jpg[/img]
to look like
[img]http://dl.dropbox.com/u/23989104/shouldlooklike.jpg[/img]
but the latter does not work, if I click anything nothing happens.

---

### Post by WeltEnSTurm on 2011-03-26
Oh god what did I do :v
```
compiz
Backend     : ini
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing move options...done
Initializing resize options...done
Initializing place options...done
compiz (core) - Error: Couldn't load plugin 'decoration'

```

```
sudo apt-get install compiz-fusion-plugins-extra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 compiz-fusion-plugins-extra : Depends: compiz-core-abiversion-20091102
E: Broken packages

```

---

### Post by Perfect Storm on 2011-03-26
Hi WeltEnSTurm

There's a Linux Mint forum to get help with your distro.
You'll find it here: [http://forums.linuxmint.com/](http://forums.linuxmint.com/)


regards
A.I. Dude
Ubuntu Forum Staff

---

