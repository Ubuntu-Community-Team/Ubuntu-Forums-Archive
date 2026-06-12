---
title: "kernel panic cant repair"
date: 2009-01-07
forum: General Help
---

### Post by mark led on 2009-01-07
Hello all! I loaded ubuntu 6.1 from a boot disk a friend from work gave me I formatted my drive so ubuntu was the only one on my hardrive. everything was great but now the system is not booting? I'm getting 
(full page of text) last line reads:
<0>Kernel panic - not syncing: Attempted to kill the idle task!
No one can tell me whats going on.

My computer is a dinosaur... I can't get into it to give you more info sorry. I'm computer illiterate and I would be greatful for any assistance.

Oh and I've tried to run form a live disk that gives me the same error. I can't reformat or anything? I've had three people fiddle with my bios and cmos settings but no one has been successful. help please. thanks in advance.

---

### Post by Den_Citronen on 2009-01-07
First off, get the latest Ubuntu 8.10. If you can't, ask your friend to make a CD with it for you.

Other than that, I know nothing other then that kernel-panics are the worst... :(

---

### Post by mark led on 2009-01-10
Well, I'm lost! I was getting a kernel panic with v6.1,so I tried to reinstall Ubuntu using live cd's 5.1,6.1,8.1 and all I get is more kernel panics! What is going on here. I've tried 3 different sets of live cd's all of them work on other computers. What am I doing wrong?

---

### Post by domoso on 2009-01-10
Could be an indication of hardware problems. Without actually looking at your system, I'm guessing, but maybe you have some bad memory? Or some hardware in your system is conflicting with drivers. Start with a really basic system: Mobo, CPU, 1 mem stick, 1 Hdd. See if that gets Ubuntu loaded. If it does then anyone of the items you took out of your system is the culprit, reinstall them one at a time until you reproduce the error. If not and it's still panicking then try different memory. If that doesn't do it, I dunno.

BTW, your system isn't OC'd is it? If so, reclock it to defaults.

---

### Post by mark led on 2009-01-10
I'm sorry? what do you mean by oc'd?

---

### Post by domoso on 2009-01-10
Overclocked

Oh and in that basic system....include a video card, forgot to mention that ;) unless it's built into the mobo, then you don't gotta worry about including it.

---

