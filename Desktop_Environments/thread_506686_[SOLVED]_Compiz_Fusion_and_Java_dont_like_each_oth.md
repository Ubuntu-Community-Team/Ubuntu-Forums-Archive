---
title: "[SOLVED] Compiz Fusion and Java dont like each other :("
date: 2007-07-22
forum: Desktop Environments
---

### Post by WinterWeaver on 2007-07-22
Noooooo.... I've been using Compiz Fusion and I love it, but now I have a dilemma.

I have 2 apps which I desperately need to use, and unfortunately they are both JAVA based.
When I run them, with compiz fusion active, it will load the window borders etc. but the inside of the window does not render T_T ....

I'll attach a screenie.

Is there anyone that know a solution/workaround for this, other than not using compiz fusion?

Thanks,

WW

---

### Post by 5-HT on 2007-07-22
There's a workaround for jre5 (append 'export AWT_TOOLKIT=MToolkit' to your ~/.bashrc), but I haven't come across any for jre6.
cheers,

---

### Post by WinterWeaver on 2007-07-22
Thanks, I will have a go at googling that.

---

### Post by WinterWeaver on 2007-07-22
Hmmm... I tried reverting back to JRE5 and ran compiz like this:

```
compiz --replace -c emerald && export AWT_TOOLKIT=MToolkit
```

Now the app doesn't even start up.... I'm gonna go back to jre6 and wait for a workaround. I'll just boot into my KDE (with no compiz) when I'm using those apps, which is gonna be annoying.

EDIT: Oh ... nvm... found out I can do 'metacity --replace', and that gets me to the normal gnome wm, so that I can run java apps.... still hoping for a workaround though.

---

### Post by WinterWeaver on 2007-07-22
Found a solution that worked for me!!

> **possessedskier said:**
> WinterWeaver - To show Java screens in Compiz:

Edit the environment file in the etc directory by typing the following in a terminal session:
gksudo gedit /etc/environment

Then add the following line below the path line:  
AWT_TOOLKIT=”MToolkit”

Save the file and exit. You may have to restart Linux, I don't remember.

YAY !! I now have Compiz Fusion and JRE6

Thanks to Possessedskier!!

WW

---

