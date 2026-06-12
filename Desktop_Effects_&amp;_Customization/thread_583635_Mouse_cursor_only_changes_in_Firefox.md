---
title: "Mouse cursor only changes in Firefox"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by mikeserv on 2007-10-20
I installed a new mouse cursor set for my desktop by unarchving the set into /home/(user)/.icons and then selecting it in Appearances --> Customize --> Pointer.  But the mouse cursor only changes for the first few seconds during login - and then reverts back to the gnome default cursor set for most operations.  It seems to use my preferred set while over some windows - like Firefox for example - but for the most part it is just the default set, still.  Has anyone else experienced this?  Can someone help me out?

-Mike

---

### Post by kerry_s on 2007-10-20
log out and back in, any time change the cursor you have to do that.

---

### Post by mikeserv on 2007-10-20
Oh, I guess I should have mentioned that I did that as well - a ton of times. 

-Mike

Edit: Although I suppose you could have inferred that I've tried that at least once after reading, *"But the mouse cursor only changes for the first few seconds during login..."*

---

### Post by kerry_s on 2007-10-20
> **mikeserv said:**
> Oh, I guess I should have mentioned that I did that as well - a ton of times. 

-Mike

Edit: Although I suppose you could have inferred that I've tried that at least once after reading, *"But the mouse cursor only changes for the first few seconds during login..."*

okay, try a reboot then.

---

### Post by mikeserv on 2007-10-20
Yeah, tried that, too.  No luck.  Thanks for trying, though.

-Mike

---

### Post by kerry_s on 2007-10-20
> **mikeserv said:**
> Yeah, tried that, too.  No luck.  Thanks for trying, though.

-Mike

okay, try moving the cursor icons to /usr/share/icons
then reselect them.

---

### Post by mikeserv on 2007-10-20
Nope, still doesn't work.  I can't figure it out - it's like something in the startup is changing the cursor.

-Mike

---

### Post by mikeserv on 2007-10-21
I was right: there was something in startup doing it!  It was compiz, because it was set to "Gconf Configuration File Backend" or something, rather than "Flat File Backend."  So I changed that, and now my cursors work.  Woohoo!

-Mike

---

### Post by kerry_s on 2007-10-21
> **mikeserv said:**
> I was right: there was something in startup doing it!  It was compiz, because it was set to "Gconf Configuration File Backend" or something, rather than "Flat File Backend."  So I changed that, and now my cursors work.  Woohoo!

-Mike

you never said you were using compiz. :mad:

---

### Post by mikeserv on 2007-10-21
Oh, well, oops.  Ok, for future reference, I'm running a fresh install of 7.10 with Compiz, Kiba-Dock, and Emerald in the startup, and sundry other things that run by default.

-Mike

---

### Post by citaworvk on 2007-10-21
Can you please explain exactly how you fixed the problem as I am currently experiencing the same situation . 

Thanks alot.

---

### Post by mikeserv on 2007-10-21
Ok, first of all do you have compizconfig-settings-manager installed?  If not, then you'd better get it.  Just search for it in Synaptic.  Once you have it, open it (System --> Preferences --> Advanced Desktop Settings) and select Preferences.  There you'll be able to choose your back-end.  For me "Gconf Configuration Backend" was selected.  I changed it to "Flat-file Configuration Backend," closed the settings manager and then restarted X (just press Ctrl-Alt-Backspace).

Does this fix your problem?

-Mike

Edit: Oh, and be prepared to go back into Compiz settings manager because any customization that you may have done will be wiped when you change the backend.  As soon as I set all of the plugins back up the way I wanted them I chose the export option (it's right on top of the backend deal in Prefs) and saved a custom config file.  Now if I have to do something like that again I'll be ready to go.

---

### Post by citaworvk on 2007-10-21
Thanx that did the trick!

---

### Post by jayde6 on 2007-10-22
I was having the same problem and your solution led me to a simpler fix. I had already exported my settings before, so after I switched to flat-file I imported them only to find the default mouse cursor back. I dug around the settings a bit and noticed that in the general options area there is a cursor box. My settings had it set to default and when I switched to flat-file it cleared the box. So when I imported my settings it put default back in the box. It turns out that your fix comes not from switching to flat-file but just the clearing of the cursor box.

---

### Post by mikeserv on 2007-10-23
Aha!  You're talking about the field "Cursor Theme" under the General tab in General Options?  Mine is blank right now, but I assume that must have read "Default" while I was having the problems...

---

### Post by jayde6 on 2007-10-23
Field, that was the word I was looking for. The whole time I was typing, I was thinking box was the wrong word, ha. Yep it seems that compiz and gnome were fighting for control over it (compiz being the victor mind you). I had changed the 'default' to the theme I wanted to use before and suffered the opposite behavior (cursor changed on desktop but not in firefox, thunderbird, etc.). It was not till you posted your fix did I even consider you could leave the field blank. Thanks for relieving my frustration :-D (it always seems to be the little things that get to me most heh)

---

