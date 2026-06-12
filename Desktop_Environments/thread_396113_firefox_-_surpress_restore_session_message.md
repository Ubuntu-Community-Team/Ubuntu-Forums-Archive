---
title: "firefox - surpress restore session message"
date: 2007-03-29
forum: Desktop Environments
---

### Post by hendoyeah on 2007-03-29
I'm trying to configure a ubuntu box to autologin and launch firefox automatically - which i have done. 
However if firefox was not closed properly the previous time the Restore Previous Session message comes up and requires user input.
I would kike to surpress this message if possible. so firefox will just start a new session no matter what.

can any one suggest a solution?

cheers

nathan

---

### Post by RaZer0r on 2007-03-29
should be some kind of ff setting, i'll check for you in a minute

Edit:
hmmz wierd, i swore i had that options somewhere, i'll look it up for you, after a quick scan i didn't find anything yet

---

### Post by orb9220 on 2007-03-29
Just go into about:config and in the filter box type in session they are all there and set
to true by default. Just double-click to change.

---

### Post by hendoyeah on 2007-03-29
thanx for your replies, 
none ofthose settings fix my prob.

thought it might have been the browser.sessionstore.resume_session_once 
but either true or false affects it. Actually none of those settings affect it.

i run a "killall firefox-bin" to shut it down and i start it up again and it gives me that message. 
I just want to have firefox start a new session every time no matter what.

---

### Post by hendoyeah on 2007-03-29
there's go to be a file or setting somewhere that can reste that promt. even if i can run a script to delete or edit a file and then launch firefox

---

### Post by hendoyeah on 2007-03-29
Got it. that was the correct setting.
i did set it to false before but firefox must be shutdown cleanly for the changes to take affect.

---

### Post by hendoyeah on 2007-03-29
Another way to do it (quite a hack- I can't be 100% sure it wont mess anything else up) but there's a sessionstore.js in your profile dir (.mozilla/firefox/<prifilename>/sessionstore.js).

if you never want to restore a session, just delete this file before running firefox each time.

...as i said - a hack, seems to work though.

---

### Post by Endolith on 2008-01-20
Anyone know of a way to default to "Restore session" after a few seconds?  It's annoying to come back to the computer expecting all my tabs to be loaded and see the dialog instead.

---

