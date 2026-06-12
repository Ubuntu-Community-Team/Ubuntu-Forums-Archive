---
title: "&quot;Normal&quot; desktop effects in Gutsy don't persist after restart"
date: 2008-01-29
forum: Desktop Effects &amp; Customization
---

### Post by infinitejones on 2008-01-29
The title says it all I hope - I enable "normal" desktop effects in Gutsy (system -> preferences -> appearance -> visual effects) and everything's fine. After restarting - not crashing or hard resetting, just normal restarting - Gnome reverts to no desktop effects and I have to manually enable it again.

This is on a fairly basic Compaq notebook with i810 graphics and 768mb of RAM (I think - at least 512mb, anyway). I don't think it's an issue with the machine being unable to handle desktop effects because it all works fine when I manually enable it. I can't enable "extra" effects but that doesn't surprise me and I'm not that bothered.

Not life or death but I'm curious about why I need to re-enable manually after every reboot - any ideas?

---

### Post by sattruckmark on 2008-01-30
I'm having the same issue with mine.  (noob here). I'm thinking that I ran into the same problem when I installed virtual box to run xp (still stuck with it).  My problem there was; after I installed it, it wouldn't let me run it because I didn't have permission.  I had to add myself as a user in the ---SYSTEM--ADMINISTRATION---USERSANDGROUPS menu.  I've also attempted to edit my GRUB config file with no success as of yet because it pops up that I don't have permission.

I'm thinking that my problem with my visual effects issue is along the same line.  I can enable it, run it without problem, but it reverts to default (none) when I reboot.  

Anybody have any ideas?

---

### Post by infinitejones on 2008-02-05
Any more ideas anyone?

---

### Post by jaytek13 on 2008-02-05
Have you tried manually saving your session? It's system->administration->sessions I believe.

---

### Post by infinitejones on 2008-02-06
That worked! Thanks!

---

