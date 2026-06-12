---
title: "Compiz strangness after Gdesklets install."
date: 2006-08-18
forum: Desktop Environments
---

### Post by smallville on 2006-08-18
Hey... Installed Ubuntu Dapper today, did all the updates, installed Xgl and Compiz (for nvidia) and everything went great, Got compiz themer, etc...even got some cool effects going on (eg. skydome, etc.) 
Anyways, I installed VLC player and Gdesklets (for the dock feature.) Everything went great, except for the annoying shading on the gdesklet dock...so, I had my fun and I booted back into windows...booted back into ubuntu to play around some more, and noticed that compiz's shortcut keys didn't work anymore. (Ctrl+Alt+Left,Right, etc.)... The cube spins if I manually click my other desktops, but the hotkeys are broken!

If anyone knows if its something I did or a way of checking a change log or something, to help identify the problem, I'm all up for it and I'd gladly appreciate the help.

If you want me to post any more info , just ask me.

Thanks in advanced,
             -Smallville

---

### Post by murataht on 2006-08-18
as long as the cube rotation is working, it does not mean the compiz is broken. maybe the short cut keys are disabled. 
there are 2 places that you can check the short cut keys. gset-compiz and gconf-editor. 

still i recommend the gconf-editor to check out the short cut keys. 

open gconf-editor, go apps->compiz->plugins->rotate->allscreens->options
there you can find rotate-left-key, rotate-right-key, ...etc. check if they specified short cut keys for them. 

also you can play with other settings, and others plugins there.

good luck.

murat

---

### Post by smallville on 2006-08-18
I checked gconf-editor and everything was correctly set-up.
But its not just the rotate hotkeys that don't work...its the rain (shift+F9), its the F12 key (re-aranges current desktop windows.) and Ctrl+Alt+LClick doesn't do anything either. All of the keyboard hotkeys aren't working. Hmmmm....

And I don't think I have gset-compiz. :\

Anything else you suggest I do? I appreciate your efforts. ^^

-Smallville

---

### Post by jackkerouac on 2006-08-18
I can't help you with your main problem, but I have two suggestions to fix the gdesklets dock problem:

1. Remove gdesklets completely and go with akimbo. Better dock, more fun.

2. (More realistic) just turn off the trailfocus plugin in Compiz. That's causing the black fade-out.

---

### Post by murataht on 2006-08-18
with googling i could not find the akimbo link. can you post the link here?

---

### Post by jackkerouac on 2006-08-19
Darn, sorry! My bad - I gave you the wrong name! It's Akamaru, not whatever the heck I wrote. The link [is here]("http://people.freedesktop.org/~krh/akamaru.git/").

---

### Post by murataht on 2006-08-20
> **jackkerouac said:**
> Darn, sorry! My bad - I gave you the wrong name! It's Akamaru, not whatever the heck I wrote. The link [is here]("http://people.freedesktop.org/~krh/akamaru.git/").

thanks. got it and tried it. very cooooollll!:cool:

---

