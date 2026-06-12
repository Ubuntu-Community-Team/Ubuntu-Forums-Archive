---
title: "how to capter ALT+TAB in vncviewer"
date: 2009-01-10
forum: General Help
---

### Post by bruce1914 on 2009-01-10
I am using Ubuntu 8.10. I have installed a Red Hat AS3 on my VMWare machine and I managed to connect to it using vncviewer on Ubuntu.
I have tried xtightvncviewer and xvnc4viewer, they work fine, but there is one more problem, I can not capter ALT+TAB on vncviewer.

When I type ALT+TAB on AS3, vncviewer would not capture it, so the result is: I can only change between my Ubuntu window and vncviewer window?

How can I make my vncviewer capture ALT+TAB so I can change my windows on AS3?

---

### Post by electrogeist on 2009-01-11
using compiz on your workstation?

---

### Post by bruce1914 on 2009-01-11
> **electrogeist said:**
> using compiz on your workstation?
Yes, I turned on compiz 3D effect.

I can capture ALT+TAB in full screen mode, but I just want to capture it even in normal mode.

When I using realVNC in windows, there is a option like:

  'pass special keys directly to server'

When I turn this on, all special keys would be passed directly to server (of course including ALT+TAB) regardless of my mode.

In its linux version, I can not find such option.

---

### Post by electrogeist on 2009-01-11
I think compiz steals it, prob workarounds if you search

Try not using alt+tab in compiz, I like using the "windows" key for most of the actions, initiates rotation with the mouse, zoom with wheel, with tab it would free up alt+tab, etc.

---

### Post by bruce1914 on 2009-01-11
I have modified the key definition of compiz, and it works. Thanks.

---

