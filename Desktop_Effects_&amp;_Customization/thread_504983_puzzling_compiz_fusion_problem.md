---
title: "puzzling compiz fusion problem"
date: 2007-07-19
forum: Desktop Effects &amp; Customization
---

### Post by amisus on 2007-07-19
So I managed to install the Linux Novell Groupwise 7 client, and it works fine...unless compiz fusion is running.  If compiz is running, then Groupwise opens, but I can't see anything.  It's just a gray window.  But looks can be deceiving.  If I click blindly, then I can hit "address book" or whatever else, and it seems responsive, I just can't see what is going on.

Also, if I start Groupwise *first*, and then run compiz fusion, then it works fine.  Unless I close Groupwise and try to run it again.  That messes it up again.

Can anyone help me to get these two play nice together in Feisty?

---

### Post by Death_Sargent on 2007-07-20
insert this in your compiz startup skript

export AWT_TOOLKIT=MToolkit

asumming that novell groupwise is java based this should solve your problem

---

### Post by amisus on 2007-07-20
Thanks for the suggestion.  Groupwise does require Java, but unfortunately when I started compiz from the console

> compiz --replace export AWT_TOOLKIT=MToolkit

groupwise was unaffected.  It's still all gray.

---

### Post by steinpt on 2007-07-21
try > AWT_TOOLKIT=MToolkit compiz --replace or > export AWT_TOOLKIT=MToolkit; compiz --replace instead

---

### Post by amisus on 2007-07-21
no dice.  Maybe I'll have to be content with metacity....

---

### Post by Death_Sargent on 2007-07-22
im sorry i was not clear

i mean something like this

```
#!/bin/bash
#
# Start compiz within gnome-session
#
if (( `ps -A -o comm | grep -c '^Xgl$'` == "1" )); then
       DISPLAY=:1 compiz
else echo "${0}: Error: compiz not launched. Xgl not running?"
fi
export AWT_TOOLKIT=MToolkit
```

or if not on xgl then this

```
#!/bin/bash
#start aigxl compiz
compiz --replace 
export AWT_TOOLKIT=MToolkit
```

or 
```
compiz --replace && export AWT_TOOLKIT=MToolkit
```

---

### Post by WinterWeaver on 2007-07-22
I'm soooo happy I stumbled uppon this thread !!! I was having the same problem, and have been searching for a solution for about 5 hours straight now!! XD

I'm gonna try your suggestions here :)

Thanks! :guitar:

WW

---

### Post by WinterWeaver on 2007-07-22
I tried this:
```
compiz --replace && export AWT_TOOLKIT=MToolkit
```[/QUOTE]

.. but unfortunately it's not working. I still have the gray window. T_T

---

### Post by amisus on 2007-07-22
Tried all three without effect.  Stubborn groupwise :mad:

---

### Post by WinterWeaver on 2007-07-22
It's not GroupWize... I'm trying to run different applications, which I need, both are Java... so it's a problem with Java and Compiz.

---

### Post by WinterWeaver on 2007-07-22
Right, someone just mentioned in my Thread ([http://ubuntuforums.org/showthread.php?p=3061702#post3061702](http://ubuntuforums.org/showthread.php?p=3061702#post3061702)), that the solutions posted here only works for JRE5.... I'm going to uninstall 6 and revert to 5 to see if that works.

---

### Post by WinterWeaver on 2007-07-22
Found a solution that worked for me!!

> **possessedskier said:**
> WinterWeaver - To show Java screens in Compiz:

Edit the environment file in the etc directory by typing the following in a terminal session:
gksudo gedit /etc/environment

Then add the following line below the path line:  
AWT_TOOLKIT=&#8221;MToolkit&#8221;

Save the file and exit. You may have to restart Linux, I don't remember.

YAY !! I now have Compiz Fusion and JRE6

Thanks to Possessedskier!!

WW

---

### Post by Weazl2000 on 2007-11-23
I just tried this today and got that grey screen. I put AWT_TOOLKIT=”MToolkit”in the startup script for groupwise /opt/novell/groupwise/client/bin/groupwise
Everything is working properly now.:guitar:

---

