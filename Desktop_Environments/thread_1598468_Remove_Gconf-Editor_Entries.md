---
title: "Remove Gconf-Editor Entries"
date: 2010-10-16
forum: Desktop Environments
---

### Post by thunk77 on 2010-10-16
Hi all,

I'm having trouble removing entries in gconf-editor (GUI).

It's not a serious problem, but for the life of me I can't figure it out and it's driving me crazy!

I have searched everywhere: manpages, internets, forums, can't find anything related.

Here's the situation: 
I installed Avant Window Navigator and it naturally created entries in gconf-editor for interface, applets etc. The thing is that when I uninstalled it the entries are still there, and yes I have deleted the corresponding folders in home/.gconf/apps. Also did a search of my filesystem for awn, avant widow navigator, avant-window-navigator etc and nothing came up. Looked in /etc, nothing. Looked in /etc/gconf, also nothing.

I know it's not a big deal and it doesn't affect my system in any way but I just have to know! I'm obsessed!

Regards

---

### Post by thunk77 on 2010-10-16
Here's a screenie..

---

### Post by asmoore82 on 2010-10-16
A few years ago, you could simply delete the files from within "$HOME/.gconf/" -
This saved my bacon on a number of occasions when I tweaked to death :D.

But the modern gconfd seems to have some resiliency features where
deleting the files while it is running has no effect.

There are 2 solutions...

1. While gconfd is running, use the command line utility `gconftool-2` with the `--recursive-unset` option:
```
gconftool-2 --recursive-unset "/apps/avant-window-navigator"
```

2. Delete the files while gconfd is not running. In other words, you have to "sneak" in
and delete them while you are not in any active graphical desktop sessions.
So either with the text console(Ctrl+Alt+F1) or in a "Failsafe Xterm session"

---

### Post by thunk77 on 2010-10-17
Sorry but I think you misunderstood me (or I didn't explain this properly) :)

I'm looking to delete the entries in the left pane of gconf editor. Their keys are deleted as you can see in the new screenshot I'm attaching.

However, the info you provided is indeed useful. Thanks a lot.
The -unset option is used to reset the key values to their default settings, right?

Boy, this looks a lot like the the Windows Registry.:P

*runs away*

---

