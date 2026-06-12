---
title: "Beryl taskbar missing?"
date: 2007-05-11
forum: Desktop Effects &amp; Customization
---

### Post by kingzasz on 2007-05-11
Hi,

I'm running Feisty with an ATI radeon x1400 (running flgrx).

I got beryl installed (disabled universe, so the older version) and XGL working.

So XGL works I believe (compiz works.. the window wobble and everything, and also the cube)

But when I tell beryl manager to use beryl, the taskbars disappear.  No other beryl things appear to work.

I've looked through every possible thread and tried everything.

Any ideas?

---

### Post by misfitpierce on 2007-05-11
From what I hear composite rendering is disabled on ATI drivers b/c ATI is slackin. I got mine working on ATI 200M but I forgot how and what I used. Just google beryl on ATI ubuntu is all I can say I did.

---

### Post by kingzasz on 2007-05-11
I figured it out.

Turns out that not all of my packages were forced to older packages, only earlier one.

In synaptic package manager, search for beryl, then make sure every one is forced to 0.2.0~0beryl1

---

