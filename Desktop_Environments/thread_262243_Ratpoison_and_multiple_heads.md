---
title: "Ratpoison and multiple heads"
date: 2006-09-21
forum: Desktop Environments
---

### Post by unless on 2006-09-21
I use ratpoison. I just upgraded my video card so that I could have two monitors. All is well in the basic installation department; my two monitors work fine. I didn't bother with xinerama or anything like that, since it's not like I'm going to be dragging programs between screens with ratpoison anyway.

I'm almost happy. There's just one thing: When I open a program on one monitor, I can't make it appear on the other monitor.

Let's say I've got full frames on each screen. In screen 1, I open xterm. Then I open Thunderbird. Then I switch to screen 2 (":nextscreen"), and I open Firefox. 

My window list now looks like this:
0-xterm
1-Thunderbird
2*Firefox

When I try to switch to program 0, that is, xterm, which isn't visible anywhere, ratpoison throws me back to screen 1 and opens xterm over there. So If I want to look at xterm and Thunderbird at the same time, I have no choice but to split screen 1... I can't move xterm or Thunderbird over to screen 2. (Unless I close a program, move over to screen 2, then re-open the prog, but that'd be goofy.)

I've googled this problem but I'm coming up empty-handed. Anybody got any light to shed?

Thanks.

---

### Post by unless on 2006-11-03
So I ended up going with Xinerama, after getting the suggestion to do so by Ratpoison's main developer on IRC.

Xinerama doesn't like to share with OpenGL, so no more GL. :( But I don't think my boss will be upset that I can't play armaggetron any more.

---

