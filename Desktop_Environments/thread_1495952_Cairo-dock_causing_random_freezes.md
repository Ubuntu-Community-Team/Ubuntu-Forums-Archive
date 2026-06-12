---
title: "Cairo-dock causing random freezes?"
date: 2010-05-28
forum: Desktop Environments
---

### Post by surfdoc on 2010-05-28
I'm just posting to see if anyone else is having this problem.

I'd been using karmic for ages with no probs. I did a fresh install of lucid when it came out and installed compiz and cairo-dock. Rather annoyingly my computer started to completely freeze. I couldn't get a shell up, I couldn't ssh from another machine and the sysrq keys didn't work (the fan picked up speed almost immediately). The freezing didn't seem to follow any pattern and wasn't happening when accessing the dock. I decided to disable compiz (and cairo-dock) to see if this helped. It did! I reintroduced compiz with no problems, but as soon as I introduced cairo-dock, I started to get the same problem.

I've not been able to find anything in the general logs to give any clues. Any help would be appreciated - I rather like having a dock.

ubuntu lucid
asus f5
ati radeon HD 3400

---

### Post by Cathhsmom on 2010-05-28
I do not have a freeze problem, but I do have a different problem when Cairo-Dock starts up.  When I reboot, the switcher applet on Cairo-Dock fails.

---

### Post by infamous-online on 2010-05-28
Try loading the dock up with just default settings, I assume you've tweaked yours a bit huh? It sounds like it using a high amount of the CPU if the fan goes to full throttle? So check to see how much memory and CPU usage it's using. Also how much RAM do you have on your machine?

---

### Post by fabounet on 2010-05-31
try with "cairo-dock -c"
some ATI drivers are definitely buggy (some Intels too unfortunately, but it's more rare)

---

### Post by surfdoc on 2010-06-01
Thanks for the tip: unfortunately I already use that option. 

Interestingly, I decided to use docky because of my problems with cairo-dock, and after less than 15 mins of running it my system froze. Maybe it's related to part of the ATI driver that only these apps use?

On a separate note, I updated my other computer, which has a NVIDIA card and that is freezing randomly too! However, I'm not even running cairo on that one.

Seems like lucid is rather unstable - maybe it's time to go back to karmic :-(

---

### Post by ndstate on 2010-06-04
I had the same problem with Cairo-dock, however Docky is not causing issues for me.

---

