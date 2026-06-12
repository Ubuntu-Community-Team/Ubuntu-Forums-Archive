---
title: "gDesklets - how to lauch program in terminal?"
date: 2008-03-02
forum: Desktop Effects &amp; Customization
---

### Post by John von Neumann on 2008-03-02
Hi all,

I'm using gDesklets in Ubuntu 7.10 and I'd like one of my launchers (using the StarterBar Desklet) to do the following:

1) open the terminal
2) run ssh
3) leave the terminal open

In the 'command field' for the launcher I've used the following:

gnome-terminal -x ssh <all the usual> &

And nothing happens. If I open the terminal and run the same command, I get EXACTLY what I want - I just don't see why it isn't working through gDesklets. Any help on the matter would be much appreciated!

[Please be gentle, this is only my second weekend with Linux!]

---

### Post by John von Neumann on 2008-03-02
Well I managed to fix the problem: removing the & works.

---

