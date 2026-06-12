---
title: "Disapearing window content in beryl"
date: 2007-04-30
forum: Desktop Effects &amp; Customization
---

### Post by mrvertigo on 2007-04-30
I am currently using beryl V.22 i believe on top of kubuntu 7.04 it seems that when i run beryl certain windows have no content (aim,some settings dialogs ect.) Everything elce seems to be working either fairly well or very well but in my line of work a missed text message can mean many upset people waiting on my return message, and the missing dialogues are a pain otherwise

Please help

---

### Post by Invid on 2007-04-30
I had the same problem and was unable to fix it. I ended up just enabling Desktop Effects (Compiz) and not looking back. Compiz supports all of the features I used on Beryl anyway.

Now if only I could figure out how to zoom away from the cube when I'm rotating desktops.

---

### Post by mrvertigo on 2007-05-10
nabody has a clue about this?

---

### Post by LuisGMarine on 2007-05-10
Here is something that you can try.  I tried this fix when I had beryl running and I would get blank windows in things like frostwire and Azureus.  This fixed all of my problems with beryl giving me blank windows.  I don't know exactly what the script does, but I just know it works.

You can probably modify this to any program that you are having blank windows in beryl.  This is the fix as it would be for the program gaim ( its what I thought you would use for aim ).  All you have to change to modify this for other programs is just change the **/usr/bin/gaim** to point to the program you want to change.

Here is the code: ( again this is for gaim, if you want it for another path just replace the **/usr/bin/gaim** )
```
#!/bin/bash
export AWT_TOOLKIT=MToolkit
export HOSTNAME=localhost
/usr/bin/gaim
```

Fire up a text editor, and save this file, name it something like gaim_fix or w/e program it is.  Put it on your desktop for testing purposes, just to see if it works or not, if it doesn't you can just delete it.  Make sure that you can execute this program, I'm using gnome, one of the ways you can do this is just by **Right-Clicking > Properties > Permissions 'Tab' > and CHECK the box that says " Execute: Allow executing file as a program"**

All you have to do is just double click it, run it in terminal , and you are good to go.  Hope this works for you.

Good Luck :guitar:

---

