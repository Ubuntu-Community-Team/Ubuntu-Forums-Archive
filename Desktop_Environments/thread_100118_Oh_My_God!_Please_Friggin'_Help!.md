---
title: "Oh My God! Please Friggin' Help!"
date: 2005-12-06
forum: Desktop Environments
---

### Post by Mosey on 2005-12-06
I was feeling gutsy (not to mention stupid) and decided to follow poofyhairguys How-to on installing Enlightenment (E16) on the Gnome desktop enviroment.

I followed all the instructions and logged into enlightenment...I don't like it. It's too soon for me to jump to something entirely new like that. I wanted to leap out of the rabbit hole and back into the warm arms of Metacity (or whatever).

So i attempted to accomplish a reverse of the directions so as to regain my former sorroundings.

In Failsafe Terminal (because I couldn't even fricking locate the terminal in Enlightenment!):

"Sudo cp /usr/share/gnome/default.session ~/.gnome2/session

Sudo gedit ~/.gnome2/session"

In the original how-to the instruction called for me to go into this file and find the line that reads:

1,RestartCommand=gnome-wm --sm-client-id default1

and replace it with a similar line for enlightenment.

So I went back to change it but in it's place was a new third line i'd never seen before:

1,RestartCommand=gnome-panel --sm-client-id default1

So I switched out one little bit (-panel) for the former little bit (-wm)

I also went ahead and sudo apt-get removed enlightenment from my system.

I also went into this file:

sudo gedit /usr/share/xsessions/Enlightenment.desktop

And erased the little bit of code he told us to add.

I then attempted to log into "Gnome"...

Everything loaded at startup except my top panel.



PLEASE!

Help me help myself.

---

### Post by rjwood on 2005-12-06
if everything is working ok, then just right click on the bottom panel and click add panel put it on the top and then right click on the top panel and add to panel and add your apps-places-system there.

---

### Post by Mosey on 2005-12-06
I only had one panel.

I'd modded my desktop to a bottom eyecandy launcher and a top panel.

No panel.

---

### Post by cwaldbieser on 2005-12-06
[QUOTE=Mosey]I only had one panel.

I'd modded my desktop to a bottom eyecandy launcher and a top panel.

No panel.[/QUOTE]
Can you hit ALT-F2 to get the "Run Program..." dialog?  If not, try switching to a virtual terminal (CTRL+ALT+F1), log in, at the prompt, type:
```

$ gnome-panel

```
If you switch back to X (ALT+F7), a panel should be there.

---

### Post by Mosey on 2005-12-06
It appears to have fixed itself. It corrected the file or something...when i log into Gnome I acts as if everything is honkey dorry.

It's fixed...

Except there is a strange new login command beneath gnome and above failsafe...

"Foo"

I dare not log into it.

Any ideas?

---

### Post by parktownprawn on 2005-12-06
do you have a file ```
/usr/share/xsessions/foo.desktop
```

if so what is the out put of ```
 cat /usr/share/xsessions/foo.desktop 
```

---

### Post by Mosey on 2005-12-07
It tells me there is no such file or directory.

---

### Post by mscman on 2005-12-07
This is just an educated guess, but seeing as how "foo" is used often to describe generic or empty files, perhaps your enlightenment login option was replaced with foo when you uninstalled enlightenment.  I'm not sure how you would go about removing this option, but it shouldn't hurt anything.

---

