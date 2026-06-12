---
title: "cairo dock and compiz launcher"
date: 2009-04-24
forum: Desktop Environments
---

### Post by andrea000 on 2009-04-24
i have done this befor but can't remember how to fix it i put
a compiz icon on cairo dock and it turned all my windows 
boarders red even if i install a new theme it stays red

---

### Post by ACMiller on 2009-04-24
> **andrea000 said:**
> i have done this befor but can't remember how to fix it i put
a compiz icon on cairo dock and it turned all my windows 
boarders red even if i install a new theme it stays red

Hey, it sounds to me that you have installed compiz with emerald. If you have done this you will probably find a program called emerald listed under system > preferences. Emerald is what displays your windows borders (also called window decorations). To go back to metacity (the other program that displays window decorations by default in ubuntu) press ALT+F2 and type:
```
metacity --replace
```
To go back to emerald at any point, just press ALT+F2 and type:
```
emerald --replace
```

I hope this helps. Cheers

---

### Post by andrea000 on 2009-04-24
I tried that and now i lost all desktop
effect's it fixed the boarders but my
desktop effect's is gone and it will
not let me re enable them.

---

### Post by ACMiller on 2009-04-25
Sorry about that, have you tried going to appearances, click on visual effects tab and selecting 'extra'? I think what happened is that metacity (which also does some very basic desktop effects) has replaced the compiz desktop effects. If this doesn't work, try pressing ALT+F2 and typing in: compiz. Hopefully this won't get you back to your red borders again!

---

### Post by ACMiller on 2009-04-25
Oh, another thing you could try which involves more GUI and less typing is installing 'compiz fusion icon' from add/remove programs. Then you need to run it: Applications > System Tools > Compiz Fusion Icon. If you right click on the blue icon that appears in the panel, you can select which program to use as the window manager (i.e. desktop effects) as well as which program to use as the window decorator / window borders (either emerald or GTK window decorator which is metacity). Give it a try.

If you decide you like the icon and you want it to run every time you startup, go to system > preferences > Startup Applications. Click 'Add' and in the dialog box that opens type 'fusion-icon' as the command, and it should start every time the computer starts up.

---

