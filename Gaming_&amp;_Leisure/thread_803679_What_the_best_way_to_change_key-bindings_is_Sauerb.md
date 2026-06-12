---
title: "What the best way to change key-bindings is Sauerbraten?"
date: 2008-05-22
forum: Gaming &amp; Leisure
---

### Post by diablo75 on 2008-05-22
I just installed Sauerbraten for the first time in several months.  I had tried it once before, but threw it away immediately because reconfiguring the keyboard and mouse seemed to be a real pain in the ***.

You hit escape, then options, key binding, click the action you have to change (up to this point, that's cool), but then you have to select the key you want to bind out of an incomplete selection of keys??  Where's "Up Arrow", for example?  Oh, and then the menu goes away completely after changing one binding, so I have to click through all the other previous menus again for every single key binding I want to change.  Brilliant.

Why couldn't they just have had you click the action, then simply press the key you want to bind?  That's the way most games do it.  You click the action, you aren't asked to then look at a big selection of keys on the screen, but instead, asked to simply press the key you're trying to bind.  Simple, right?

I'm assuming the next best way to do this is via a console window somewhere, where I have to type my own bindings in.  This is even less intuitive than clicking through the incomplete selection of keys in the gui thing.

Sorry to sound so cranky, but this is the reason I didn't even want to attempt playing the game last time I installed it.

So what should I do?

---

### Post by zoubidoo on 2008-06-16
Same problem here.  Also hoping for a solution...

---

### Post by spacelem on 2008-08-05
Get a feel for the config file
vim ~/.sauerbraten/config.cfg

Now put commands you want into the autoexec.cfg
vim ~/.sauerbraten/autoexec.cfg

You want lines like
bind "key-to-press" [some command]

You'll probably have to read [http://sauerbraten.org/docs/config.html](http://sauerbraten.org/docs/config.html) for help. It's not quite as difficult as they could have made it, but years of editing my Quake3 config file have hardened me.

---

