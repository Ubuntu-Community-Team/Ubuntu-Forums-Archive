---
title: "no 1280 x 1024 option after installing windows xp"
date: 2009-05-28
forum: General Help
---

### Post by Amrooz on 2009-05-28
Hey all!
I need some help with the screen resolution.
After re-installing windows xp, I tried increasing the screen resolution to 1280 x 1024 like the way it was before, but found the maximum has become only 1024 x 768 pixels.
I tried installing the latest software chip thing for my Acer from the CD that came with it and from the internet, but it's still not working!
Can anybody help me?
Thanks a lot!

---

### Post by munky99999 on 2009-05-28
No 1280 x 1024 option in ubuntu I would presume?
[http://linux.die.net/man/5/xorg.conf](http://linux.die.net/man/5/xorg.conf)

Should be the first step in determining the problem. Should verify that it is all working well. Dont be discouraged by that page. The actual xorg.conf wont be that detailed :)

---

### Post by elysianfields44 on 2009-05-28
Locate the xorg.conf file:

sudo gedit /etc/X11/xorg.conf

Scroll down to the part called "Section Screen", then within that section you should see "SubSection Display", there will be different "Modes" - you will want to add "1280x1024", so that it looks something like this:


Section "Screen"
[INDENT]Identifier      "Default Screen"
Monitor         "Configured Monitor"
Device          "Configured Video Device"
SubSection "Display"
[INDENT]Depth   16
Modes           "1280x1024"      "1024x768"      "800x600"       "640x480"[/INDENT]
EndSubSection
Defaultdepth    24[/INDENT]
EndSection


Then save the file and restart. Hope that helps.

---

### Post by Amrooz on 2009-05-28
Thanks guys for your help, but to be honest I'm not that expert with computers! Like how do I locate the xorg.conf file to start the whole process of adding the stuff to it?? :D

---

### Post by merlinus on 2009-05-28
Open a terminal window and type this:

```

gksudo gedit /etc/X11/xorg.conf

```

That will open xorg.conf.  Add the lines suggested as to screen resolution, save the file, and restart your computer.

---

### Post by Amrooz on 2009-05-28
Should this be working in windows XP? Because I'm trying and it's telling me that "it's not recognized as an internal or external command, operable program or batch file" :S

---

### Post by merlinus on 2009-05-28
Whilst in ubuntu, go to Applications/Accessories/Terminal, and type the command at the prompt in the window that opens. and press Enter.

A text editor will open with the contents of the xorg.conf file.

But before opening the text editor, make a backup of the file so you can recover it if things get worse.

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_old

```

These commands will require you to enter your ubuntu password.

You can copy-and-paste these commands as well, but use the Edit menu in Terminal for pasting, or press Shift+Ins.

If, however, you are unsure of what you are doing, then best not to do it.

---

