---
title: "All settings on Compiz Config Settings Manager (ccsm) wiped out on reboot !"
date: 2013-10-24
forum: Desktop Environments
---

### Post by shantiq on 2013-10-24
this has been happening a lot recently    first on 13.04    then now on 13.10


all my settings wiped out on reboot!
all commands and keybindings   and now unity settings too




anyone having similar?


clues to fix this please..    thanx    shan

---

### Post by mc4man on 2013-10-24
Well there is a history of 'commands' that are user set in the compiz commands plugin disappearing, usually at some point 1-3 days after being set.
(usually the command goes poof, sometimes the binding, I had a bug on this quite some time ago to no avail.

As far as other unity/compiz settings I've had no issue but your's may be different. (except edge flip, see next post

Myself only have used 1 command consistently - it allows picking a window group from all workspaces to the scale spread screen, eg. if I have FF windows  open on several workspaces the key binding will pull them all to the spread screen.

I finally got tired of having to reset all the time & conveniently there was a change in 13.10 compiz that I disliked, ( ctrl+alt+delete opening sys monitor instead of logout), so I used that to do what I'd been meaning to try - integrate the command into compiz instead of user set.

That has worked quite well, several  weeks & the command/binding has never gone away.

It's not that simple to do & needs to be done in source, give me an example of command(s) you'd like & I'll take a look. (assuming you mean the commands plugin

---

### Post by mc4man on 2013-10-24
Something else you can try concerning any setting not involving commands plugin - (may work for commands but I believe not that effective

set whatever
Then in ccsm go Preferences > plugin list > disable 'Automatic plugin sorting' (read the warning & keep in mind for future edits or re-enable before changing bindings, then again disable

Sometimes you'll also need to move a plugin where settings are being unset below the unityshell plugin using > highlight it > arrow icon down
(a classic example of this is the edge flip move in rotate or wall plugins

---

### Post by shantiq on 2013-10-25
thanx Mc  :]]]


so here are the ones that always disappear now

[ATTACH=CONFIG]247221[/ATTACH][ATTACH=CONFIG]247220[/ATTACH]


and so trying your suggestion   see how that goes...

[ATTACH=CONFIG]247219[/ATTACH]



This used to happen    "the disappearance" from time to time    but now it is just silly    so fingers crossed this might "cure"  it

---

### Post by mc4man on 2013-10-25
You'll likely lose them after a while, as mentioned about the commands plugin.
If so it seems those 3 commands could just as well be done in system settings > keyboard > shortcuts > custom commands.
(in 13.10 unity custom commands set in ^ won't take affect till you log out/in

---

### Post by shantiq on 2013-10-26
yes it did not stick will    go the other route   thnx
PS    i should av thought of that; used before forgot it is was there

---

