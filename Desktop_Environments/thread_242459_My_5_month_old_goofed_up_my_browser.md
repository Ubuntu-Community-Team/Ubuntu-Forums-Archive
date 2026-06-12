---
title: "My 5 month old goofed up my browser"
date: 2006-08-23
forum: Desktop Environments
---

### Post by yaddoshi on 2006-08-23
While I am immensely proud to have a five month old girl who is already heavily addicted to Ubuntu via my laptop, this addiction comes with consequences.  The drool is minimal, thankfully, and the fingerprints can be easily removed with an anti-static wet-wipe, but I'm not entirely sure what she did to my browser.  I do worry a bit about my hard-drive as she literally will push half of her body up on the keyboard and starts pounding the keys and the touchpad.  And she keeps crawling off with my wireless mouse.

Unfortunately, I now have a minor but annoying issue that I am embarassed to say I can't figure out.  Previously I could easily use the Up, Down, PageUp and PageDown keys on my keyboard to scroll up and down in Firefox when browsing pages.  Now, for some reason, I get a blinking cursor on the page when I attempt to use these keys, and it always jumps to the top or bottom of the page unless I first select some text.  Also, whenever I click on a link a blinking cursor appears next to it, and remains there if I go back to the page I clicked.

Again, this is a minor annoyance, but it does not appear to be just a Mozilla issue because I'm starting to see similar behavior in other programs.  Perhaps this is something in Nautilus?  I have yet to find anything under System>Preferences>Keyboard or System>Preferences>Keyboard Shortcuts, and Assistive Technology Support is not enabled.  I also couldn't find anything under Firefox Preferences or File Manager Preferences that relate to the issue, but maybe I'm missing something.

Anyway, any help would definitely be appreciated, because it's the sort of annoyance that will eventually make me format and reinstall, and I'd prefer to avoid that if I can.  Thanks!

---

### Post by Dr. Nick on 2006-08-23
Before I refrormated and reinstalled I would boot off a live cd and see if the behavior persisted. I have never seen that problem before, or any options on how to set it. 
 
It could just be a stuck key or something, who knows. That seems like a far off chance but it may be possible

---

### Post by az on 2006-08-23
> **yaddoshi said:**
> 
that will eventually make me format and reinstall, and I'd prefer to avoid that if I can.  Thanks!

Show the hidden files and folders in your home directory and delete the .mozilla one (if there is a .firefox one, kill that, too)

You will start off fresh with a brand new config the next time you run FF.

You could type "about:config" in the address bar in firefox and play with the zillion different configs (probably one of those is screwed up) but ...  It's just easier to zap it.

---

### Post by meng on 2006-08-23
I believe the problem could be fixed by this:
Edit > Preferences > Advanced
uncheck Allow text to be selected with keyboard.

---

### Post by yaddoshi on 2006-08-23
Oddly enough the zap worked, although I renamed .mozilla to mozilla_backup, then imported my bookmarks.  I had thought of trying this, but for some reason when I renamed the .firefox folder (in user/.mozilla/) it didn't allow me to reopen Firefox, so I figured that idea was out.

Anyway thanks for the help!

---

