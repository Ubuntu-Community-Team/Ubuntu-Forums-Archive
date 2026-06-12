---
title: "Still no titlebars using Beryl"
date: 2007-07-08
forum: Desktop Effects &amp; Customization
---

### Post by crhumber on 2007-07-08
I've read every post I can about using Beryl and having no titlebars, but nothing seems to work for me.  I've got nvidia geforce 7600gs and I've added all the appropriate lines to xorg.conf according to most posts, but the problem remains.  All the other effects of beryl work great, but I can't figure out the titlebar thing.  I tried switching to compiz fusion but it didn't work period for me, so I'm trying beryl again.  Can someone please help? thanks

---

### Post by ajmorris on 2007-07-08
> **crhumber said:**
> I've read every post I can about using Beryl and having no titlebars, but nothing seems to work for me.  I've got nvidia geforce 7600gs and I've added all the appropriate lines to xorg.conf according to most posts, but the problem remains.  All the other effects of beryl work great, but I can't figure out the titlebar thing.  I tried switching to compiz fusion but it didn't work period for me, so I'm trying beryl again.  Can someone please help? thanks

can you post the output from a terminal of, after starting beryl, emerald --replace please

---

### Post by crhumber on 2007-07-09
"emerald --replace" doesn't give any output after i start beryl.  the terminal just kind of freezes until i change something.  although, i think i found a fix, at least temporary.  For those of you out there still struggling with this even after adding all the recommended lines to xorg.conf, try downloading the window manager Heliodor.  Thanks!

---

### Post by hotstovejer on 2007-07-09
In your xorg.conf, under screens, what is your defaultdepth? I had a problem with no title bars, and changed it from what it was to 24, and never had that problem again. Try that, and let us know how that works!

Jer

---

### Post by crhumber on 2007-07-10
Thanks for the reply, but I've already tried that.  Everything seems to be working ok using Heliodor, which for now is just fine.

---

