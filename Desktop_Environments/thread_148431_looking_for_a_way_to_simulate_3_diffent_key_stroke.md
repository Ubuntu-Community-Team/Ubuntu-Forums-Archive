---
title: "looking for a way to simulate 3 diffent key strokes with one key (kinda macro)?"
date: 2006-03-22
forum: Desktop Environments
---

### Post by zeltak on 2006-03-22
hi guys!

i use amarok alot. i love to use the keyboard options for rating my songs and then press next song. id love to have a way to press just one keyboard combo (IE the win key+m) to have it emulate 2 other key strokes (win+2 and next) into one.is anything like this possible?

thx 

zeltak

---

### Post by ltmon on 2006-03-22
Hi,

I'm not sure of any direct way to do this, but most KDE apps are scriptable.  You could write a script to do the action, and then bind the script to a key combo using "khotkeys".

The first step to writing a script is to see what actions in AmaroK are scriptable.  If you type into a terminal "kdcop" a program show up. 

Find "Amarok" in the main tree view of kdcop, and have a poke around underneath it to find the functions you can call remotely on amarok.  You can even double-click on the function name to give it a test.  Once you have found the functions you want to call it's nearly trivial to write a script to call them in turn.

Post back here if you can get that far :)

Cheers,

L.

---

### Post by ltmon on 2006-03-23
Now I'm home I can look it up myself and give you specific instructions.

Start khotkeys by going to System Settings and clicking on "Regional & Accessability" -> "Input Actions".

Click on "New Action" and then name it something descriptive (e.g. "AmarokRate1ThenNext").  

The "Triggers" tab will let you set a keyboard shortcut for your new action (or even a mouse gesture or voice recognition trigger!!!).  

In the "Actions" tab you can set up the actions the shortcut will perform.  First click "New" -> "DCOP Call".

The remote application should be "amarok", the remote object "player" the called funtion should be "setRating" and the argument should be "1" (or 2,3,4,5).

When this is done you should create a second action, again a "DCOP Call".  It should have the application "amarok", the remote object "player", the function should be "next" and there should be no argument.

And that's it... the keyboard shortcut will rate the current track as "1" and skip to the next track.  You will need to set up further actions for ratings 2, 3, 4, 5 .... but that's easy now.

Cheers,

L.

---

