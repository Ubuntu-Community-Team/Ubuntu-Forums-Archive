---
title: "Problem with Kubuntu startup"
date: 2005-12-30
forum: General Help
---

### Post by leiffi on 2005-12-30
At startup the "kubuntu" text shows up with a meter underneath it. When the meter's full, the screen goes bezerk. A pattern of white dots appear and then it changes to a pattern of vertical pink lines and then nothing happens.. I don't know what's causing it but as a windows user, it resembles a wrong resolution setting. 

Please help!

---

### Post by daller on 2005-12-30
[QUOTE=leiffi]At startup the "kubuntu" text shows up with a meter underneath it. When the meter's full, the screen goes bezerk. A pattern of white dots appear and then it changes to a pattern of vertical pink lines and then nothing happens.. I don't know what's causing it but as a windows user, it resembles a wrong resolution setting. 

Please help![/QUOTE]

You are probably right!

Try to start in recovery-mode (press escape when grub loads!)

Then run "sudo dpkg-reconfigure xserver-xorg", and choose the right resolution! (It asks a lot of other questions, but the "right" answer is those per default!)

---

### Post by leiffi on 2005-12-30
Got it to load everything, but then it loads to the "text" list, like a DOS view. it stalls at something that has to do with batteries? I don't know.. Maybe I should just give up, shoudn't it work easily after installing?

---

### Post by One Quick Question on 2005-12-30
KDE can change the screen resolution when it loads, so I imagine if you deleted ~/.kde/config/kcmrandrrc (or edited it to say "ApplyOnStartup=false") then that should correct the problem.  If what I'm thinking is correct.
Although I can't think of how KDE would be applying the wrong resolution in the first place, so maybe that isn't the problem.
Test and see!

---

