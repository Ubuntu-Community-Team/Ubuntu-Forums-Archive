---
title: "Fluxbox Menus"
date: 2005-11-07
forum: Desktop Environments
---

### Post by knaps on 2005-11-07
Hi everyone, I just installed Fluxbox for the first time in Breezy, and I was wondering just how I might get the custom menus to work? I edited the ~/.fluxbox/menu file according to the syntax that's already in there, but restarting Flux just gives me the same default menu of xterm, restart, and exit.

Any help would be greatly appreciated.

---

### Post by kvidell on 2005-11-07
[QUOTE=knaps]Hi everyone, I just installed Fluxbox for the first time in Breezy, and I was wondering just how I might get the custom menus to work? I edited the ~/.fluxbox/menu file according to the syntax that's already in there, but restarting Flux just gives me the same default menu of xterm, restart, and exit.

Any help would be greatly appreciated.[/QUOTE]
First: Great avatar!
Second: I believe you have to edit some... fluxbox profile somewhere...

I er... Haven't used fluxbox in a _very_ long time so I'm not sure, but I know there's a place in one of the config/profile files in your home directory, ~/.fluxbox (I think), where you define your menu file.
Right now it's set to the global one, you need to change that line to be the one in your personal fluxbox directory.
- Kev

---

### Post by kvidell on 2005-11-07
Found it!
~/.fluxbox/init

edit this line:```
session.menuFile:   ~/.fluxbox/menu
```
Yours will say something about /usr/local or something, some global menu file.
Change it to look like what I've pasted.
- Kev

---

### Post by Xian on 2005-11-07
Start with the menu generation command then make edits.

```
$ fluxbox-generate_menu
```

---

### Post by knaps on 2005-11-07
Okay, I looked at my init file and it claims that the default menu is ~/.fluxbox/menu. As far as the /usr/share/fluxbox/menu file, it doesn't exist. I've edited the ~/.fluxbox/menu and restarted flux multiple times, but to no avail.

As far as the fluxbox-generate_menu command, that doesn't exist either. Commands that start with flux are fluxkeys, fluxconf, fluxmenu, fluxbare, and fluxbox. I tried poking around in fluxmenu but it just gives me errors involving GTK when I try to click on any of the buttons (no command line params for this, it's straight GUI)

So I'm really scratching my head about this now... Input?

---

### Post by Xian on 2005-11-07
[QUOTE=knaps]So I'm really scratching my head about this now... Input?[/QUOTE]

Post the contents of this file:

/home/username/.fluxbox/init

---

### Post by Xian on 2005-11-07
Okay, I've got it figured out. 
Debian really gets on my last nerve sometimes. :)

You first need to correctly edit that ~/init file.
Look for these lines (substitute your user name):

```
session.menuFile: /home/xian/.fluxbox/menu
<snip>
session.keyFile: /home/xian/.fluxbox/keys
```

Next, you have two methods to populate the menu.

1. Use the debian menu package.

```
$ sudo apt-get install menu-xdg
```

2. Unzip the file /usr/share/doc/fluxbox/fluxbox-generate_menu.gz in /usr/bin, make it executable, and then just issue the command I gave you previously. I prefer this method as it is more established and works on most distros. 

```
$ sudo fluxbox-generate_menu
Menu successfully generated.
Use fluxbox-generate_menu -h to read about all the latest features.
$
```

---

### Post by knaps on 2005-11-08
Beautiful. Worked like a charm, thanks a ton Xian!

---

