---
title: "Customizing Compiz Command-Line Arguments"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by El Chupacabras on 2007-10-19
**Background Info:**
Okay, I've been having nasty glitches all over the place whilst using Compiz Fusion on Gutsy. Back when I had Feisty, I installed Compiz Fusion using Treviño's Packages, and hacked together a Fusion-Icon that allowed me to use the Copy Texture option through the Fusion Icon. Everything Worked great. I no longer need to use that, because my Nvidia GeForce 7600 GS card has enough memory to handle a buggy, mediocre driver.

All was well, until I had to upgrade to Gutsy. I uninstalled Trev's Compiz, and reinstalled the old, decrepit Ubuntu version, then I upgraded. Everything went smoothly.After installing cssm (and thinking to myself *Geez, this utility is easy to use, why isn't it on by default?*), I set up Compiz to my liking.

However, It's a bit slow when creating or moving windows. Playback on sound and video lags when I move windows around, which it NEVER used to do. Apparently, Compiz Fusion is being launched with --loose-binding. --Loose-binding may increase the frame rate, but it causes glitches with full-screen windows, and causes  sudden slowdowns that last for a few seconds, but are annoying. It also causes my CPU usage to spike more often than in instances when it is off.

**Question:**
Can someone tell me how I can stop Compiz from launching with --loose-binding? There is no reason why I should use an option for indirect rendering when my card is more than good enough to render directly.

---

### Post by c.dric on 2007-10-19
There are a few options that you can turn on/off in /usr/bin/compiz ...

If the option you need is not there, you have the possibility to add your favorite command line arguments in that same file.

I had to turn indirect rendering on for my 64mb card and it worked like a charm.

I hope it works for you.

---

### Post by El Chupacabras on 2007-10-19
Thanks! I had attempted to edit that, but I was unsure if the --loose-binding option was in there, and the syntax highlighting in VIM went nuts after a regular expression halfway down the file.

In any case, thank you. I was really bugged by that whenever I watched videos.

---

