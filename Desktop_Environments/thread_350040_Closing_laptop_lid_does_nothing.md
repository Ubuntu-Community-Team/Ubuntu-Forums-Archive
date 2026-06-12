---
title: "Closing laptop lid does nothing"
date: 2007-01-31
forum: Desktop Environments
---

### Post by Mets on 2007-01-31
I'm trying to get my laptop to go into "Suspend" when I close the lid, and I seem to be having some problems with what I imagine is a very easy task.  I go to Power Management and select what I want to do on the lid close action.  However, when I close the lid, absolutely nothing happens.  No hibernate if that is selected, no suspend, I can't even get the blank screen option working.  Oddly enough, if I got to Quit and then hit suspend, suspend will work.  Any ideas?

---

### Post by Mets on 2007-01-31
anybody?

---

### Post by makara.aktee.sok on 2007-01-31
I do not have a laptop so I cannot test it, but... 

My theory is that, 
when the lid is closed, a key is sent to the system... The problem is, ubuntu is not assigned to do anything when that key is received! 

a) how to know what key is sent
terminal > xev

pretty cool gadget, when you press a key, it returns the "keycode". for instance, my "a" letter output this: 
KeyPress event, serial 32, synthetic NO, window 0x2800001,
    root 0x52, subw 0x0, time 2071322453, (220,-32), root:(1162,554),
    state 0x10, keycode 38 (keysym 0x61, a), same_screen YES,
    XLookupString gives 1 bytes: (61) "a"
    XmbLookupString gives 1 bytes: (61) "a"
    XFilterEvent returns: False

so, when I press the letter "a", it's actually keycode 38, and ubuntu is outputting it as "a".

so, try knowing what key is sent. 


after that, read this. 

[http://linux.omnipotent.net/article.php?article_id=11801](http://linux.omnipotent.net/article.php?article_id=11801)

and then, do this

[http://www.codejacked.com/create-custom-keyboard-shortcuts-in-linux/](http://www.codejacked.com/create-custom-keyboard-shortcuts-in-linux/)

you'll have to figure out yourself what is the command for suspend, lock, hibernating. 
I'll let you figure that one out =).

---

### Post by Mets on 2007-02-03
Thanks a lot, I'll check that out!

---

