---
title: "[SOLVED] CPU Graph"
date: 2008-04-28
forum: Desktop Environments
---

### Post by Zeotronic on 2008-04-28
I upgraded to 8.04 recently, and I don't like the new CPU Graph... sure its essentially the same as the old one, but if I wanted a bar beside my CPU Graph, I would use the CPU bar of the System Load Monitor. Does anyone know how to turn the bar off, or a way to get the old CPU Graph back?

Edit:

Besides that the new graph seems shorter.

---

### Post by morgengenuss on 2008-04-29
i completely agree: the bar (or in my case, as i have a dualcore, the two bars) is utterly unnecessary.

if there is a way to switch back to the old cpu-graph i would definitely go for it...

---

### Post by pro003 on 2008-04-29
what's exactly wrong with new cpu graph? to me - it's even prettier and better...

if you want to, you can always install a sreenlet with various cpu activity graph...

---

### Post by Zeotronic on 2008-04-29
> what's exactly wrong with new cpu graph? to me - it's even prettier and better...

Well I don't know how it could be prettier, (unless maybe you are using the new 'grid' visual) but on my end its roughly 6 pixels shorter than it was... oh its probably just as wide, but the short-ness is killing me! In morgengenuss's case it makes a bit more sense to have a bar for each processor, and I'm assuming the graph is the total use... but in my case the single bar is just re-iterating what the graph is already telling me... and its taking up further space to boot. Perhaps you have saw my kind before, but I'm one of those people that shvitz out over wasted screen space. (and as a result only have one panel) Like the System Load Monitor has the option to turn any of it's bars on or off, the new CPU Graph should have the option to turn the bar(s) off.

> if you want to, you can always install a sreenlet with various cpu activity graph...
Screenlets, are those the things that sit on the desktop? I never liked those.

I'm going to see if I cant download the source from Xfce and compile and install it with, if nessisary, my own modification.

Edit:

Ok... I cant seem to find it. I'm sure its there, I just cant find it.

---

### Post by morgengenuss on 2008-04-29
i found the source [here]("https://launchpad.net/ubuntu/+source/xfce4-cpugraph-plugin/0.3.0-1ubuntu1") but to be honest i don't want to install 50 packages just to compile it.

i thought i'd be going for gutsy's .deb but packages.ubuntu.com seems to be down at the moment...


edit: actually i found the deb of gutsy [here]("http://de.archive.ubuntu.com/ubuntu/pool/main/x/xfce4-cpugraph-plugin/xfce4-cpugraph-plugin_0.3.0-2ubuntu1_i386.deb"). i first removed the new xfce4-cpugraph-plugin and then installed the old one and i can tell you it feels great :)

---

