---
title: "I have lost all my firefox bookmarks!!!!!!!!!!!!!!!!!!!"
date: 2009-02-15
forum: General Help
---

### Post by svsig on 2009-02-15
There was a Firefox update quite recently, I am not sure if it was after this update or after I executed a "sudo apt-get autoremove" command that I lost my bookmarks, but this should not have happened anyway. 

I have experienced this before after a Firefox update. I am quite new to Ubuntu, and I find this bloody annoying! I have been quite happy with Ubuntu for about a year or so, but if I experience this kind of instability repeatedly I think I will have to go back to Windows because I find this really unacceptable. 

Is there some way I can get my bookmarks back?

---

### Post by williane on 2009-02-15
Not sure if you can get them back but I recommend using google bookmarks. You can install the toolbar and have a dropdown on your PC just like FF.

Plus you still have access to them on any PC, any OS, and don't have to worry about backing them up.

---

### Post by Dr Small on 2009-02-15
Having apt run autoremove should not have done this, and I don't believe that it did.

---

### Post by bettlebrox on 2009-02-15
Firefox stores your bookmarks in a file called bookmarks.html in a sub-directory (named after your FF profile name) under:

[FONT="Courier New"]~/.mozilla/firefox[/FONT]

"sudo apt-get autoremove" will not touch any files in your home directory, only files directly installed by a package.

---

### Post by jwbrase on 2009-02-15
I have been fairly disappointed with Firefox on Ubuntu, although for different reasons. I just went and installed Opera, which I'm finding that I really, really like.

I'm not sure about your problem, but I blame my problems with Firefox on Ubuntu more on Firefox than Ubuntu, so I wouldn't go back to Windows just because of Firefox.

---

### Post by svsig on 2009-02-16
Well, at least I got my bookmarks back, thanks to beetlebrox, but I don't like this. Firefox is not stable. Maybe I should try Opera.

---

### Post by bettlebrox on 2009-02-16
It's weird that it doesn't automatically find your bookmarks. I wonder if it's created a new blank profile and wasn't reading your previous profile.

Was there more that one directory in ~/.mozilla/firefox ?

---

### Post by mkvnmtr on 2009-02-16
Opera doesn't seem to want to install on my 9.04 but on my Mint distro it seems to be much more stable and nicer to use than Firefox. If you can install it you should at least try it. Features are different so it might not be for you but it is great for me.

---

