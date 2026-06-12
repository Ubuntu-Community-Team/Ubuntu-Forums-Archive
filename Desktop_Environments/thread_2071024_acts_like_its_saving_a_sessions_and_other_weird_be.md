---
title: "acts like its saving a sessions and other weird behaviour"
date: 2012-10-14
forum: Desktop Environments
---

### Post by vectorthorn on 2012-10-14
some thing happened over night, while nothing was updated afaik, where,  when i log out, and log back in, or even restart the computer, it opens  every thing i previously had open. the problem is, i DONT want this, and  it is disabled as far as i can tell.

it also seems to be  crashing compiz, or something, because after compiz starts and loads my  wallpapers and backgrounds, it LOOKS like it tries to start again, and  DOES start, but looses all its settings.

i DO have compiz setup  to start at startup, but not the rest of the programs. also, this has  been working fine for several months now. it just started happening when  i came back to my desk this morning. i also noticed i now have a CORE  of my processor missing, even down at the bios level [o_0] - but that  should not affect the desktop environment, because i still have 5  cores...

... hmmm, it's possible there is some settings manager that is screwed up, but if so, i would not know where to look.

here's a quick video of the problem:
[http://www.youtube.com/watch?v=hg1EiW4f54s](http://www.youtube.com/watch?v=hg1EiW4f54s)

any help would be appreciated, TIA.

---

### Post by The Cog on 2012-10-14
Try changing the checkbox "Save session for future logins" which is actually on the logout dialog box, where you choose logout, shutdown etc..

---

### Post by vectorthorn on 2012-10-14
it's not enabled to begin with.

here's a quick video of the problem:
[http://www.youtube.com/watch?v=hg1EiW4f54s](http://www.youtube.com/watch?v=hg1EiW4f54s)

---

### Post by The Cog on 2012-10-14
Ah. The logic is a bit twisted. Try this:
* Close all your applications, leaving as empty desktop.
* Log out, making sure that "save sessions" chekbox is checked. This will save the fact that you want to start up with no applications running.
* Log back in and next time you log out, make sure the check box is not checked.

I think it always restores the saved sessions, so you have to save the fact that you want an empty desktop.

---

### Post by vectorthorn on 2012-10-14
i'll try that. it may possibly always save a session, but i never had this problem from it before.

btw, is there a way to DESTROY ANY EXISTING SESSIONS, and remove any options to observe any kinds of sessions, other than the active session? in other words, is there a way to delete all sessions, and don't save future sessions?

=== edit ===
i gave that a try, and it did not work. compiz still does not work  correctly on start up, and nautilus still launches on start up. it looks  like i'm going to have to completely reinstall xubuntu :-\

---

### Post by vectorthorn on 2012-10-14
Delete me

---

### Post by vectorthorn on 2012-10-14
i THINK i fixed it. it's behaving as expected again. here's what i did:

01: make sure "save session" is turned off etc etc
02: logout
03: [ctrl][alt][f1] to go to a terminal without x
04: login (user name, [enter], password, [enter])
05: $ rm -Rf ~/.cache/sessions/*
06: $ exit
07: [ctrl][alt][f7] to go back to x login
08: login
if (you use compiz){
  09: go to active session in the startup and settings manager to view running programs
  10: set xwm4 to "never" to prevent it starting up (interferes with compiz)
  11: logout
  12: login again
}

---

### Post by The Cog on 2012-10-14
Sweet. Thanks for posting the fix. It had me puzzled.

---

