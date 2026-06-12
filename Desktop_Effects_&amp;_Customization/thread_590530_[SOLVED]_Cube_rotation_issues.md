---
title: "[SOLVED] Cube rotation issues"
date: 2007-10-24
forum: Desktop Effects &amp; Customization
---

### Post by tencent on 2007-10-24
I can rotate my cube using ctrl+alt+button 1 without issue and I can rotate using ctrl+alt+left or right. My issue is that when using the ctrl+alt+left or right it skips sides. So if I have windows open on virtual desktop 1 but I am viewing virtual desktop 2 one would assume that ctrl+alt+left would take me to virtual desktop 1 instead it typically flips me to virtual desktop 4 or 3. Furthermore it doesn't always skip 2 sides but sometimes 3 and sometimes 1 so there seems to be sense to the madness. I've tried looking through the forums and google and I can't seem to find anyone talking about this. Any idea? I have tried to fix it with CCSM and GConf but I can't find anything to cause it.

edit * I think it flips to sides that have open windows but I find this really annoying, I know I didn't have the issue in 7.04. Also zooming out ctrl+alt+down works but I have the same problem when I try to move left or right, it just seems to randomly skip sides of the cube regardless of open windows on the cube or not.

---

### Post by tencent on 2007-10-26
am I the only one that has this issue?

---

### Post by vasiliymeshko on 2007-10-26
Same here, and I find it pretty frustration. Anyone can suggest a fix?

---

### Post by vasiliymeshko on 2007-10-26
Found and fixed.

I was using the old 'GL Desktop' If that is the case, remove it (in Synaptic it's gnome-compiz-manager) and install compizconfig-settings-manager. Everything works as expected now. Hope the same works for you too.

---

### Post by tencent on 2007-10-26
unfortunately that did not resolve the issue. I even tried completely uninstalling all of the compiz packages and reinstalling with compizconfig-settings-manager instead of gnome-compiz-manager and I still have the same issue. Any other ideas to try out?

---

### Post by tencent on 2007-10-26
finally figured it out.. desktop wall switcher was conflicting with rotate cube causing my problems.

---

### Post by semateos on 2008-03-18
Same issue, how exactly did you solve the conflict with wall switcher?

Thanks!

---

### Post by tlink on 2008-03-18
If you go to System > Preferences > Advanced Desktop Effects Settings  
you can not only find the said desktop wall that is probably conflicting with the cube, but also customize a lot of other plugins.

---

