---
title: "Is there anyway to temporarily turn off Compiz-Fusion?"
date: 2007-07-19
forum: Desktop Effects &amp; Customization
---

### Post by BlahMan_of.Doom on 2007-07-19
Whenever I want to play Counter-Strike, I wanna get the best framerates, so how do you exactly turn off Compiz Fusion?

---

### Post by amadeus266 on 2007-07-19
Here's what I did:

Create two shortcuts on your panel
shortcut #1: Start Compiz   code: compiz --replace &
shortcut #2: Stop Compiz   code: metacity --replace &

When you want compiz running, click shortcut 1, shortcut 2 when you don't.

---

### Post by FleetAdmiral74 on 2007-07-19
If Fusion is anything like Beryl, then there should be a setting somewhere to use an alternative desktop manager. If its not...well then, go with the above solution :)

---

### Post by BlahMan_of.Doom on 2007-07-19
> **amadeus266 said:**
> Here's what I did:

Create two shortcuts on your panel
shortcut #1: Start Compiz   code: compiz --replace &
shortcut #2: Stop Compiz   code: metacity --replace &

When you want compiz running, click shortcut 1, shortcut 2 when you don't.

Haha, ok. Thanks.

---

### Post by hyperair on 2007-07-20
Remove those ampersands (&). Those are only useful in the terminal. Otherwise they're there for no reason. In fact, there've been cases where something or rather got confused and refused to execute the command because of the &, if I'm not mistaken.

---

### Post by Moonfrost on 2007-12-15
> **BlahMan_of.Doom said:**
> Haha, ok. Thanks.

I also came here for the same thing! that worked awesomely well! thanks!

---

### Post by n1ght28 on 2008-04-07
Amazing job amadeus266, worked better than i could hope for, cheers,

---

### Post by MemoryDump on 2008-04-07
you could also use [Compiz-Switch]("http://ubuntuforums.org/showthread.php?t=662926")

---

