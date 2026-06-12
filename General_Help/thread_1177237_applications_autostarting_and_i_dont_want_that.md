---
title: "applications autostarting and i dont want that"
date: 2009-06-03
forum: General Help
---

### Post by unix1adm on 2009-06-03
Afer upgrading from 8.x to 9.x when i login all the applications that i had running come back up. This is a pain as I am not always on-line and my mozilla keeps starting as well as my tty session. I dont want this.

I want just a clean desktop. I went into the preferences and startup applications and unchecked the remember desktop apps.


However things still start up.

What am I missing here?

Also how can I recover all the Mozilla tabs i had. Since I killed mozilla it lost all it stabs that i went to. I would like to recover several (like 10 tabs).

---

### Post by unix1adm on 2009-06-03
i did figure out how to keep mozilla from losing tab going forward just not how to recover what i had before. guess ill have to try to find my info the hard way.

---

### Post by unix1adm on 2009-06-03
I foudn this but looks like he never got a solution either

[http://ubuntuforums.org/archive/index.php/t-1123128.html](http://ubuntuforums.org/archive/index.php/t-1123128.html)

---

### Post by unix1adm on 2009-06-04
still no one has a resolution to this. I have done plenty of searches and cannot seem to find a solution

may be some download later on will fix it.. i guess its a nuisance ill have to live with

---

### Post by rax_m on 2009-06-04
Have you looked at System->Preferences->Startup Applications?
On one of the tabs it has an option similar to "Remember what applications I had running"

---

### Post by unix1adm on 2009-06-06
yes that was the first thing i looked at. it is not selected.

---

### Post by Brandon Williams on 2009-06-06
After you've disabled remembering the current session, you might need to delete the previously remembered session data in order to get rid of it. Check in ~/.cache/ and delete anything that looks like it might be related to this problem. I'm guessing that the startup applications would probably be in a directory called gnome-session. You can safely delete the whole ~/.cache directory if you want to make sure you get every possible culprit. It's a good idea to do that from a console login, rather than a graphical login.

---

### Post by unix1adm on 2009-06-08
before i go deleting anything in the dir hear is what is there. does not look like much..

lt:~/.cache$ ls
compizconfig
event-sound-cache.tdb.165ef2a8e8489a2b07e88358495a7fb2.i486-pc-linux-gnu
notify-osd.log
rhythmbox
tracker

---

### Post by Brandon Williams on 2009-06-08
Nothing there looks like it would be causing the problem. The full lists of places that I can think of where you might find something that would lead to an application being started are: ~/.cache/, ~/.config/autostart/, ~/.xprofile, ~/.profile, ~/.xsessionrc, ~/.gnomerc, ~/.xsession, ~/.Xsession, and ~/.xinitrc. You've checked ~/.cache. Have you checked all of the others?

---

### Post by CatKiller on 2009-06-08
When you've not got anything running, you can use Alt-F2 -> gnome-session-save to remember that you want it to start without anything running, as opposed to now where you've got it starting with all the things that were running when you told it to remember them.

---

### Post by dnairb on 2009-06-08
I posted a solution to the startup programs issue a few weeks ago:

[http://ubuntuforums.org/showthread.php?p=7292241#post7292241](http://ubuntuforums.org/showthread.php?p=7292241#post7292241)

---

### Post by unix1adm on 2009-06-09
I tried that but i got a Run Application popup 
It did not do what you described.

---

### Post by CatKiller on 2009-06-09
> **unix1adm said:**
> I tried that but i got a Run Application popup 
It did not do what you described.

Are you saying that you pressed Alt-F2 and got a Run dialogue, or that every time you log on you get a Run dialogue?

---

### Post by unix1adm on 2009-06-09
when i press alt f2 i get a run dialog box.

---

### Post by unix1adm on 2009-06-09
I just saw this in your posting. and it seemed to work for me.. Thanx

"OK, this works on my system:

System --> Preferences --> Startup Applications.
Options tab.
Make sure that "Automatically remember..." is ticked.
Close.

Close all applications not required at startup.

Log off, then back on.

No applications should be running.

Go to Startup Applications, Options again, and this time ensure that "Automatically remember..." is not ticked and then close."

---

### Post by CatKiller on 2009-06-09
> **unix1adm said:**
> when i press alt f2 i get a run dialog box.

That's what you were supposed to get. So that you could run gnome-session-save.

Glad you got it sorted, anyway.

---

