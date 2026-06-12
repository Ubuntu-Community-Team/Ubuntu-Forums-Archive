---
title: "Lost my menu panels."
date: 2006-12-06
forum: Desktop Environments
---

### Post by Johnny_Sparx on 2006-12-06
Hello, 

I just upgraded to 6.10 and have had alot of the problems ironed out.  All of a sudden however, I just logged in and found that the panel that has my menu in it as well as the notification area on the bottom of my desktop has gone!

I am sure it is a quick fix, but am a little disoriented after an hour of messing around trying to get things fixed.

Any help in this department is well appreciated.

JS

---

### Post by aidanr on 2006-12-06
try in a terminal "killall gnome-panel"

switch to a different tty (ctrl-alt-F6) (ctrl-alt-F7 to switch back) if alt-F2 isn't working

---

### Post by philipgm on 2006-12-06
I have also had this problem but it seems to go away with a restart of gdm or when persistent a reboot of the machine. I haven't found a way to stop it happening and if anyone has any ideas please share.

---

### Post by ^rooker on 2006-12-07
Unfortunately, I was able to top your mistake:
Most of my items located on the top panel disappeared!! 

I tried restarting X - didn't help.
I tried rebooting - didn't help.

...it's persistent! eeeek!

I KNOW that all my items are still there, because I can see their entries in .gconf/apps/panels/ but I can't figure out how to fix this. I've already spent some time on digging myself through gconf's XML structure, but maybe if someone could give me a hand here - I'd be more than happy.

I don't want to delete/add everything again, because I want a solution that can help others, too!

Here's how I got into that dilemma:
(My system: Ubuntu 6.06.1 with kubuntu-desktop also installed)
1) I had a drawer on my top panel with a few icons in it. One of them was a link to an URL.
2) I drag&dropped an entry from my "Applications" menu to that drawer - and I seem to have dropped it right on the URL link.
3) An errormessage appeared - which I don't exactly remember, but it was something like "expected an int" (guess it wanted an integer?)

That's it. menu, drawers, shutdown-button: GONE.
(The panel and "some" icons however are still there - bottom panel unaffected)

any ideas?

---

### Post by Gen2ly on 2006-12-08
Hmm, the exact thing that happened to me.  Blanked on the panel are the menu, couple links i put there, window switcher, and drawer.  Noticed there was a software update but didn't apply it yet.  Whats going on?  Is there a way to rebuild this or something?

---

### Post by Gen2ly on 2006-12-08
Oh, i think I figured it out!  I was using the notify scheduler as a seperator. :|
When that software update came up the panel must have freaked out.  Plus I had everything locked down.  I just right clicked and remade the panel again.

---

