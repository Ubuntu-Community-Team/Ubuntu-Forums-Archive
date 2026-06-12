---
title: "What is this Screenlet?"
date: 2010-11-30
forum: Desktop Environments
---

### Post by sandman3838 on 2010-11-30
Hello

If you would please take a look at this screen shot that I have attached here.  I came across this online but I haven't been able to find anything on it.  I'm interested on the items that I have marked with a red X.  Is this some sort of Screen-let theme package?

Thank you for you time and help.

---

### Post by karthick87 on 2010-11-30
That's conky i guess.

---

### Post by mister_p_1998 on 2010-11-30
Guess again...
not gdesklets either, I reckon a screenlet

---

### Post by kerry_s on 2010-11-30
**sudo apt-get install screenlets**

[http://www.screenlets.org/index.php/Home](http://www.screenlets.org/index.php/Home)

---

### Post by quyvuong00 on 2010-11-30
[IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]yes, i'm using conky, but i can't run multy conky, help me, how to install multy conky!!!:oops:

---

### Post by stinkeye on 2010-11-30
> **quyvuong00 said:**
> [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]yes, i'm using conky, but i can't run multy conky, help me, how to install multy conky!!!:oops:
To run multiple conkys, instead of using the command **conky** to  load 
your config you name each config something like conky1, conky2 etc.

Then to run you use 
```
conky -c /path/to/conky1
```
The **-c** option tells conky to load a config file instead of $HOME/.conkyrc

If you just run "conky" it loads the config **~/.conkyrc**.
If there is no ~/.conkyrc file it will load a sample config at /etc/conky/conky.conf

So after giving your configs different names you would use a script added to startup applications to start your conkys.
eg```
#!/bin/bash
sleep 20 &&	# 0 good for Xfce - use 20 to 30 for Gnome
conky -c ~/Conky/conky1 &
sleep 3 &&
conky -c ~/Conky/conky2 &
```

[**_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")

---

### Post by sandman3838 on 2010-11-30
Thank you all for the information.

But, I think its screenlets also!
However I have screenlets installed already and what is shown in the desktop screen shot is not part of the base package.  

The search continues!
If I find anything I'll let you all know.

---

### Post by stinkeye on 2010-11-30
> **sandman3838 said:**
> Thank you all for the information.

But, I think its screenlets also!
However I have screenlets installed already and what is shown in the desktop screen shot is not part of the base package.  

The search continues!
If I find anything I'll let you all know.

They look like gDesklets which I don't think is actively developed anymore.

---

### Post by sandman3838 on 2010-11-30
Ya!  You right is was Gdesklets!
I tried it for a little bit.
It must be older.......  I didn't like the interface very much.

That and when you install it there are only 4-5 GDesklet items installed in the program.  A Calendar a clock and two other items.  

Seemed weak!

Still thanks for all your help.

---

