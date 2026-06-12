---
title: "HOW TO: Make GDM -&gt; Gnome login seamless"
date: 2009-01-22
forum: General Help
---

### Post by blazemore on 2009-01-22
This script will make GDM keep its wallpaper until Nautilus draws its own.
To install:
```
sh install
```

to revert:
```
sh revert
```

---

### Post by blazemore on 2009-01-23
Please can someone test this. It's working fine on my machine.
cat the scripts before you run them if you're not sure.

---

### Post by HunterK on 2009-01-23
Ahhh, is this so you don't get that brief screen of solid color after logging in but before getting to your desktop?

---

### Post by blazemore on 2009-01-25
correct

---

### Post by aslamp on 2009-01-25
Works for me =]. Did you consider the scenario that someone's not using the default Human login theme?

---

### Post by blazemore on 2009-01-26
Well, actually, I'm looking for a way to take this into account.

---

### Post by billgoldberg on 2009-01-26
Once you perfect it, let the Ubuntu devs know about your hack.

---

### Post by blazemore on 2009-01-26
I think it can be done, but I don't know how to do the shell scripting required. Someone more knowledgeable than me could maybe look at the files to see the changes I've made, and work out a way to implement this across all themes?

---

### Post by leewebb on 2009-01-27
I was going to attempt the custom theme part, but then a quick search in the forums brought up the following thread which appears to do what you're after: [http://ubuntuforums.org/showthread.php?t=753261](http://ubuntuforums.org/showthread.php?t=753261)

(Can't vouch for it myself, but plenty of other people have OK'd it.)

---

