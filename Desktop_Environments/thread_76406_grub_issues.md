---
title: "grub issues"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Jack000 on 2005-10-15
Hi

I'm a fairly new linux user trying to set up dual boot with windows on my machine. I'm having a very specific problem that doesn't make a lot of sense to me.

I've tried to boot by adding the following line to menu.lst:

title		Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd0,0)
makeactive
chainloader +1
boot

didn't work

then I figured maybe that whole mapping thing wasn't necessary, so I tried this:

title		Windows XP
rootnoverify (hd1,0)
makeactive
chainloader +1

same thing.

out of desperation, I booted (and failed) with the first setting, and then edited it in grub to the second setting, and voila, it works.. I've found that I can successfully boot to windows if I try method 1, get "error 13", return to the grub menu, then edit the lines to method 2 and boot in that exact sequence. Method 2 directly from menu.lst doesn't give me an error, it just stops.

For now I'm stuck doing this little tap dance every time I want to boot to windows.. Can anyone help?

thanks

Jack

---

### Post by mosquito-liu on 2005-10-15
you try&#65306;

title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
chainloader     +1


:o

---

### Post by manicka on 2005-10-15
try

title           Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by Jack000 on 2005-10-15
Hi, and thanks for the replies

Maybe I doing something really dumb.. but I read on the grub docs that rootnoverify is needed to boot windows instead of root, and that because windows doesn't like to be on hd1, I have to do a virtual swap between hd0 and hd1 - hence the mapping thing.

manicka:
I have ubuntu installed as default on (hd0,0) and windows on (hd1,0), so wouldn't that boot up ubuntu? Correct me if I'm wrong :]

mosquito:
am I making a really noobish mistake? feel free to correct me

thanks

---

### Post by SilentCacophony on 2005-10-15
> title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
chainloader +1

Since you have Windows on the second drive, this answer looks correct to me. Even though you tell grub to remap the drives around, you still have to use the correct hardware reference for the drive when specifying the *root* line. The *map* lines are only designed to 'fool' Windows into thinking it's on the first drive. They don't affect how grub sees it.

EDIT - misquoted

---

### Post by manicka on 2005-10-15
[QUOTE=Jack000]H
manicka:
I have ubuntu installed as default on (hd0,0) and windows on (hd1,0), so wouldn't that boot up ubuntu? Correct me if I'm wrong :]
thanks[/QUOTE]

sorry, my bad, didn't read your post properly

try

title = Windows XP
root = (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

---

### Post by Jack000 on 2005-10-16
thanks a lot, that fixed it! edit - this really should be mentioned in the docs for beginners...

now I have yet another question if no one minds :]
When I try rebooting in windows, it doesn't seem to register as a "reboot". I'm having problems with this because certain apps (extfs support, win update) requires that I reboot, but after I shut down and boot up, it still says that I haven't rebooted.

I've always thought reboot = shut down and start up. But maybe that's not the case?

thanks for all the help

Jack

---

### Post by manicka on 2005-10-16
What do you mean by it doesn't register as a reboot. What message are you getting? I've never seen a message that says 'you didn't reboot'.....curious

---

### Post by Jack000 on 2005-10-16
basically, I went to windows update and got the critical updates. I would like to get some optional updates as well, but the site said that I needed to first reboot. I rebooted and went on the update site, the same message was there.

I installed extfs to read my ubuntu drive, but couldn't figure out why it wasn't working. After a while I read the docs and found that the error I was getting was associated with not having rebooted after install. I did shut down and restart, but every time it's the same error.

that's what leads me to think the reboot wasn't "registered"

any ideas?

---

