---
title: "why  can't apps get along? wanting Amarok AND Kaffeine"
date: 2005-10-30
forum: Desktop Environments
---

### Post by jacknel on 2005-10-30
hey guys, total newbie question, but why is it that we can't have certian apps installed at the same time...

I just tried to install amarok and it is askin to remove Kaffeine amoung other things... is there no way for them to coexist?

---

### Post by jmcnaught on 2005-11-01
hmmm... I have amarok and kaffeine both installed (both with the gstreamer engine).  What engine are you using?  If you don't know, it's gstreamer.  In Synaptic I was poking around at the dependencies for amarok and kaffeine, and I don't see a conflict.

maybe you could do this:  open a terminal and type:

sudo apt-get install amarok

Enter your password when prompted.  It will show a bunch of text output about what is going to get installed/removed etc.  Because something is going to get removed, it will ask if you're sure.  Answer no.  Then copy and paste the text output into a reply here.

That information will help to figure out what's going on there.

---

### Post by bionnaki on 2005-11-01
what asked you to remove kaffeine?
never seen apt/synaptic tell me that I needed to *remove* anything...

---

### Post by dtfinch on 2005-11-01
It wants to remove things very often. If a prerequisite is removed or updated to a version newer than what it knows the package supports, it'll demand that the package be removed, even if you believe the combination ought to work.

---

