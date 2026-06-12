---
title: "Openbox with fbpager?"
date: 2008-09-30
forum: Desktop Environments
---

### Post by e2k on 2008-09-30
Is it possible to use fbpager with openbox? I can start it, and it shows 4 desktops, but it doesn't show any windows I have open? Anyone else having this problem?

```
$ fbpager -v
FbPager 0.1.4: (c) 2004 Henrik Kinnunen (fluxgen<at>fluxbox.org)
```

---

### Post by urukrama on 2008-09-30
I've tried it a while ago and remember it didn't quite work (though I can't remember what exactly didn't work; probably what you talk about here). 

Instead I use bbpager (in the dock), or netwmpager (on the desktop). There is also an obpager.

---

### Post by e2k on 2008-10-01
Yeah apparently it just refuses to co-operate. I installed netwmpager though, seems fast and simple.. Now how would I go about to move it to an other location than the upper right corner? Couldn't find any documentation on how to conf it, and the config-example doesn't seem to have any entry for placement.. :-s

---

### Post by urukrama on 2008-10-01
> **e2k said:**
> Now how would I go about to move it to an other location than the upper right corner? Couldn't find any documentation on how to conf it, and the config-example doesn't seem to have any entry for placement.. :-s

Change the following line:

```
geometry = "80x21+2+3"
```

The first two numbers give the size of netwmpager, the second two the x and y position (you can also use negative numbers for that).

---

### Post by e2k on 2008-10-01
Thanks, that did the trick! :)

---

