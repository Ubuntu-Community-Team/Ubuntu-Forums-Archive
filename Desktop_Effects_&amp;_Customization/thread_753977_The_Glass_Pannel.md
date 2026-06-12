---
title: "The Glass Pannel"
date: 2008-04-13
forum: Desktop Effects &amp; Customization
---

### Post by Firm18 on 2008-04-13
Hello!

I really want customize my desktop with new glass panels (vista type) but I have no idea how to do it. Is it possible to get panel looking like this in Beryl?:

[http://gnome-look.org/CONTENT/content-pre1/57352-1.jpg](http://gnome-look.org/CONTENT/content-pre1/57352-1.jpg) 

If not, how do I install Compiz and make the panel look like the one in the link. I am new with Ubuntu so please make it easy ^^

Cheers


Firm.

---

### Post by Zorael on 2008-04-13
Do you mean the bottom panel or the glassy titlebars and borders around windows? I'm confused.


And if you're running Gutsy, you should use Compiz anyway; Beryl is old and superseded by it. :>

---

### Post by Firm18 on 2008-04-13
I am using Feisty, and I mean the main panel with the Application and etc. (The bottom one in the screen)

---

### Post by Zorael on 2008-04-13
[Have a look at this.](http://gnomestyle.blogspot.com/2007/05/make-ubuntu-look-like-vista.html)

---

### Post by Firm18 on 2008-04-13
But it doesn't tell me about the glass panel effect ^^

---

### Post by tylerspaska on 2008-04-13
It is unclear to me if you just want the vista panel or if you want the entire look. Anyway I'm going to assume you just want the panel. To do that best I would install compiz and emerald. Compiz is better than beryl anyway and would make a good replacement. 

There is a "how-to" for installing compiz-fusion (and emerald) from git. I can't remember the link right now, but if you search the forums for "compiz git" I'm sure it will be one of the first 13 threads or so. 

It works on feisty, but I would make a few changes. If you are already using metacity you won't need to do step 2 (if you don't know what you're using then do step 2, it can't hurt), and for step 3 remove each of the components one at a time. Some of them aren't installed in feisty and if you just enter a long string it will return an error and nothing will be removed.

When you're done installing from GIT use the emerald themes manager and there are tons installed by default - several of wich look like the vista panel.

If you have any questions, let me know.

---

### Post by Firm18 on 2008-04-13
whenever I do: CCSM it says:
Bash: command not found

What should I do?

Also when I write Compiz in terminal it does:

/usr/bin/compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
/usr/bin/compiz.real: No manageable screens found on display :0.0

---

### Post by Zorael on 2008-04-14
You know, I'm still confused.

[list][*]The "glass panel" is the panel which the guide describes how to install, aye? The black thing?
[*]You need to install the **compizconfig-settings-manager** package to get ccsm.
[*]As the message says, you should run it with the --replace argument to have it replace the currently running window manager.
```
$ compiz --replace
```[/list]

---

