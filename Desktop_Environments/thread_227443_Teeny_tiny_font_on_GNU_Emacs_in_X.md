---
title: "Teeny tiny font on GNU Emacs in X"
date: 2006-08-01
forum: Desktop Environments
---

### Post by LadyDoor on 2006-08-01
Hi there,

So I tend to run emacs in a terminal (emacs -nw) when I need to edit a file...the reason for this is that previously in X (when I used Breezy), I got weird rectangles instead of text. Now, in Dapper, the problem is not so serious...instead, I merely have itty-bitty text that is effectively illegible. Does anybody know of a way to increas the font size just in X? Oh, and here's a screenshot and my .emacs.el file.

---

### Post by neoeden on 2006-08-01
Is this a picture of a terminal window or of a virtual terminal (ctrl+alt+F1)?

---

### Post by LadyDoor on 2006-08-01
Neither. This is an Emacs X window. The font and everything is fine both on a TTY and in an XTerm. My question is about Emacs run in an X window.

---

### Post by neoeden on 2006-08-01
Oh, shows how much I know about emacs. Maybe this is your issue?

[https://launchpad.net/distros/ubuntu/+source/xfonts-core/+bug/45823](https://launchpad.net/distros/ubuntu/+source/xfonts-core/+bug/45823)

Have you tried changing the font that emacs uses? Something like:

[http://www.linuxhelp.net/guides/emacs/](http://www.linuxhelp.net/guides/emacs/)

I'm a vi fan myself, else I'd be able to help more.

---

### Post by LadyDoor on 2006-08-01
Aha! Thank you very much.

---

