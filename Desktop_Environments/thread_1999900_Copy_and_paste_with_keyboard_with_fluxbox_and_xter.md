---
title: "Copy and paste with keyboard with fluxbox and xterm"
date: 2012-06-08
forum: Desktop Environments
---

### Post by kerryhall on 2012-06-08
I know copy and paste can depend on the window manager as well as the terminal. I'm running Ubuntu 11.10 in a virtual machine on a MacBook. I want to be able to select text in xterm, and use a keyboard shortcut to cut/copy/paste (as Macs are severly short on mouse buttons) into firefox or vi running in xterm, and vice versa. Thanks!

---

### Post by hakermania on 2012-06-08
Hello, I'm not 100% sure that this will work, but have you tried:
a) Selecting text in terminal using Shift+Ctrl+C
b) Pasting to any **other **program with Ctrl+V
or
a) Copying from **other **program with Ctrl+C
b) Pasting to terminal using Ctrl+Shift+V
?

---

### Post by kerryhall on 2012-06-12
Keep in mind that I am using xterm, not gnome-terminal.

shift-ctrl-c in xterm sends a ctrl-c command to the terminal, so no this does not work.

Thanks!

---

### Post by kerryhall on 2012-06-19
Bump

---

### Post by yeah1234 on 2012-06-26
I was looking for an answer to the same question and found one that works for me.

Use middle click to copy and paste, which is just clicking the left and right mouse buttons at the same time. 

First highlight whatever you want to copy like you normally would and then go to where you want to copy it to and middle click. Seems to work fine for me. Just copied something from a terminal to an email and that worked fine. I'm using Debian Squeeze not Ubuntu, but I don't think that matters.

Nevermind, I just realized you had a Mac. There is probably another way to do it. You could always setup ssh and just ssh into your VM from the Mac and then just use the Mac commands to copy and paste.

---

