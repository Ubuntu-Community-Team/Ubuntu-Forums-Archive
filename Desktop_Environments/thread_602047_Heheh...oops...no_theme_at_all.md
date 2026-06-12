---
title: "Heheh...oops...no theme at all"
date: 2007-11-03
forum: Desktop Environments
---

### Post by Gideon147 on 2007-11-03
I had to go back to Feisty for a little bit (long story, but had to stay away from compiz).

Installed emerald and selected the theme I wanted...nothing happened. Another thread with same problem recommended a user type emerald --replace

Well I did. As soon as I hit "Enter" I had no window decoration at all. Can someone A) Tell me what happened so I don't do it again and 2) Advise on how to reverse this?

Thank you

---

### Post by Thyme on 2007-11-03
Hi Gideon147,

Remember that emerald requires compiz to be installed. What is the output when you type in "emerald --replace"?

---

### Post by arthpix on 2007-11-03
Seems like something related with enabling composite, with my Nvidia card I had to add two options, "addargbglvisuals" and "composite enable" (something like that) in xorg.conf. Don't know about ATI cards, but try to search about that.

---

### Post by JBAlaska on 2007-11-04
to get back where you started, hit Alt-F2 and type;
```
metacity --replace
```

As Thyme mentioned, you need a composit manager (like compiz) to run Emerald.

---

