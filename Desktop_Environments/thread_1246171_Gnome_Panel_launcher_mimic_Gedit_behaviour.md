---
title: "Gnome Panel launcher: mimic Gedit behaviour?"
date: 2009-08-21
forum: Desktop Environments
---

### Post by hictio on 2009-08-21
I have the usual app launchers on my top Gnome Panel.
Now, I have noticed something regarding the one that launches Gedit, something that I want to reproduce on, say, the one that starts Firefox.

When you click on the Gedit icon, it lauches the program, but, if you click on it again, it doesn't launch a new instance of Gedit, it even un-minimizes an already opened Gedit window, if open, when you click on the Panel's icon (with extra functionality if you have an opened tab!)

Now how can I do the same with Firefox and Evolution? I really hate that they start a new instance when I click their icons by mistake.
I'm pretty sure this is an option of the program itself, and if so, any idea how can I have that on my Firefox and Evolution?

TIA :D

PS:
I know that there are other programs that resemble the Os X Dock and do this, but I would like to do this using the same Gnome Panel.

---

### Post by ajgreeny on 2009-08-21
Have a look at the properties of the launcher (right click) if you have not already done so and see if you can get a clue from the command used in that, or at least the suffix to the command, maybe %x, where x is some other letter.

Not something I've even thought about before, but it's a good question and has made me curious.

---

### Post by hictio on 2009-08-24
Been testing some options a bit.
For the Firefox launcher, changed to this:

```

firefox -no-remote %u

```

Now, if the Firefox Gnome Panel icon is clicked, and there is an already running Firefox, it'll print this: 

[URL=http://img19.imageshack.us/img19/2712/notanotherfirefox.png]
[IMG]http://img19.imageshack.us/img19/2712/notanotherfirefox.th.png[/IMG]
[/URL]

And won't launch a new one.

---

