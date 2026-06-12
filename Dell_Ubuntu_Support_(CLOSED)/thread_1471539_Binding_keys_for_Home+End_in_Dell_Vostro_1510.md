---
title: "Binding keys for Home+End in Dell Vostro 1510"
date: 2010-05-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by snarko on 2010-05-03
I'm using Dell vostro 1510 laptop and i just installed Ubuntu 10.04 Lucid Lynx, Gnome. 

I'm not sure what they were thinking at Dell but this model is missing the Home and End keys (Home and End are available with Fn+Left/Right arrow). This is very annoying and I'd like to try key binding that will assign  the rarely used NumLk and Pause to act at Home and End*. 
However, it wouldn't let me do this specific  binding  (System->preferences->keyboard shortcuts).

Am I doing something wrong or that it is impossible to make these specific key reassignments?

Thanks! 


*it worked well on the MS-XP installation using a AutoHotKey script.

---

### Post by snarko on 2010-05-06
OK - so here is what works in an awkward way. 

Apparently the ubuntu 10.04 doesn't have a .xsession file. 
so I created the file (I called it .xsession but the actual name doesn't matter as you'll see):
> 
#!/bin/bash
sleep 3
xmodmap -e 'keysym Num_Lock = Home'
xmodmap -e 'keysym Pause = End'
For some reason, the ubuntu restores the old key binds on start up (from where? why?) so changed took affect only for one session. 

The workaround for that was to add the .xsession to the list of startup application programs (unser System->Preferences) and it works. 

The sleep at the begining of the script waits a few seconds,  allowing it to run in a short delay in case there is another script that restores default bindings. 

If you have a more elegant solution please post.

---

