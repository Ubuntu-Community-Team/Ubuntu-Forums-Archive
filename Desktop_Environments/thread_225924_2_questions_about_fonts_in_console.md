---
title: "2 questions about fonts in console"
date: 2006-07-30
forum: Desktop Environments
---

### Post by conexion200 on 2006-07-30
Hello

1. I know that dpkg-reconfigure console-data allows to set keymap for console. But what should I use instead "console-data" to modify fonts for terminals? (or I have to modify /etc/console-tools/config manually)

2. How to avoid flickering during start and font change? I know that it is caused by file /etc/init.d/console-screen.sh.

---

### Post by moopere on 2006-09-24
> **conexion200 said:**
> Hello

1. I know that dpkg-reconfigure console-data allows to set keymap for console. But what should I use instead "console-data" to modify fonts for terminals? (or I have to modify /etc/console-tools/config manually)

You have probably already worked this out - but it hit me today and in searching for an answer I hit your post.  The way to setup your console fonts again (edgy) is to do a:

dpkg-reconfigure console-setup

This will ask you everything, fonts, keyboard, keys, blah

Cheers,
Craig

---

### Post by Ramses de Norre on 2006-09-24
is it also possible to change the color of the console font?

---

