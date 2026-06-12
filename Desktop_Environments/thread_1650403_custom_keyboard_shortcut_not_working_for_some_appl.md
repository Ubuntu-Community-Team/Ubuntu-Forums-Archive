---
title: "custom keyboard shortcut not working for some applications"
date: 2010-12-21
forum: Desktop Environments
---

### Post by coyoterunner on 2010-12-21
Hello, i am trying to set some custom keyboard shortcuts using compiz in the commands section...but it is not working. For example , i want to use kaffeine and i am using as command the word kaffeine.  When i use it in the custom commpand of compiz it is not working at all. Just to be sure that the command is indeed "kaffeine" i execute it via terminal using the word "kaffeine" and it is executed normaly. I am 100% sure that the command is only for terminal use and as general launcher. The same behavior is observed for other applications. The strange thing is that when i want to put a custom keyboard shortcut in compiz for a python script then the command "python xxx.py" is working!


What i am doing wrong?


--C

---

### Post by oarion7 on 2010-12-21
If you try and set the python script to load in place of Kaffeine; in other words, using the same key combination, does it work? It may be possible that the key stroke you are trying to use is having a conflict with some another application.

**What key combination are you trying to use?**


Also, if you run **gconf-editor** and then navigate to **/apps/metacity**, are the values you set for the keystroke and command reflected in "global_keybindings" and "keybinding_commands" respectively?

---

### Post by coyoterunner on 2010-12-21
Well i am using the same keyboard shortcuts for the python script and the kaffeine. I have used a lot of combinations...none of them worked.

I did not used gconf-editor because i am setting the shortcuts from compiz in order to set also some screen edges shortcuts (neither the screen edges are working for kaffeine...).

 I am pretty sure that the command kaffeine must be somewhat different to work ...:mad:


EDIT: i checked gconf editor.. the commands are set as in the compiz commands...

---

### Post by oarion7 on 2010-12-21
> **coyoterunner said:**
> Well i am using the same keyboard shortcuts for the python script and the kaffeine. I have used a lot of combinations...none of them worked.

I did not used gconf-editor because i am setting the shortcuts from compiz in order to set also some screen edges shortcuts (neither the screen edges are working for kaffeine...).

 I am pretty sure that the command kaffeine must be somewhat different to work ...:mad:

Well, any options you set in the Compiz Config Settings Manager should be stored in gconf-editor as well, automatically. It might help to look there and double check.

Edit: If kaffeine really isn't loading that way, but other things are, you could *try* creating a bash script that loads kaffeine and then pointing to that in the keyboard shortcut command.

---

### Post by coyoterunner on 2010-12-21
Your damn quick!
I chekced that gconf-editor has the same shortcuts.

I dont know if this helps, but the little application x-tile works also when i set it in the compiz shortcuts...strange!

---

### Post by coyoterunner on 2010-12-21
Strange but when i disabled compiz then the keyboard shortcuts worked...but now i cannot use screen edges...whats happening????

---

### Post by oarion7 on 2010-12-21
Funny, I just downloaded and started using x-tile a few nights ago. Discovered it on accident while I was looking for something else.

Try this. Run from the terminal:

```
nano kaffeine.sh
```

Then right click and paste into the file:

```

#!/bin/sh

kaffeine &

exit
```

Now type CTRL+x, then "y" to save.

Now go to a terminal and type:

```
chmod +x kaffeine.sh 
```

Now try running the command **./kaffeine.sh** from the terminal. If it works, try setting **./kaffeine.sh** as the command for your keyboard shortcut instead of [b]kaffeine[b].

If that doesn't work, there might be something particular about Kaffeine I don't know about that is required in launching it. In that case:

run **alacarte**

look for the launcher for kaffeine (assuming you have one) and edit it to see if "kaffeine" is indeed the exact command.

**EDIT:**

> **coyoterunner said:**
> Strange but when i disabled compiz then the keyboard shortcuts worked...but now i cannot use screen edges...whats happening????

Well, what keyboard shortcut are you using? Compiz by default comes with a number of other keyboard shortcuts that might be conflicting. If you re-enable Compiz, does it work now?

Compiz might just have needed to reboot.

---

### Post by coyoterunner on 2010-12-21
It worked!!!! but why???? i had used the command kaffeine & with no success!!! why i had to wrap it in a bash script? 

Thx a lot for your time. You made my day.

---

### Post by oarion7 on 2010-12-21
> **coyoterunner said:**
> It worked!!!! but why???? i had used the command kaffeine & with no success!!! why i had to wrap it in a bash script? 

Thx a lot for your time. You made my day.

I have *no* idea. Just tried any random workaround that "might" work and I guess it did! Maybe someone else can shed some light on the why.:D

Glad to help.:popcorn:

---

