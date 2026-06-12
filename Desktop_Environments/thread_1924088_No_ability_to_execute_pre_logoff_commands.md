---
title: "No ability to execute pre logoff commands"
date: 2012-02-11
forum: Desktop Environments
---

### Post by sleepyhollows on 2012-02-11
Hi all

What im trying to do is shutdown virtual box when the users logs off.

I've been looking high and low, and can't seem to find a solution.

I'm pretty dumb founded that Gnome doesn't provide a pre log off hook?

Gnome very nicely gives Virtual box a chance to prompt the user, but I would like to execute the save state commands BEFORE G'nome has signalled VBox to close.

PostSession does not acheive this.

Any ideas?? :)

Mic

---

### Post by sleepyhollows on 2012-02-11
I found a nifty python script that hooks into the gnome api

[http://www.linuxquestions.org/questions/linux-desktop-74/gnome-run-script-on-logout-724453/](http://www.linuxquestions.org/questions/linux-desktop-74/gnome-run-script-on-logout-724453/)

Only problem is that it receives the 'save-yourself' signal at the same time vbox does, and therefore vbox is prompting to close when my vboxmanage command runs, which locks up the VM.

Oh well.

---

