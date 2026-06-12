---
title: "emacs under lynx becomes unresponsive"
date: 2010-05-27
forum: Desktop Environments
---

### Post by bobdobbs on 2010-05-27
I just upgrqaded to lynx, and now I'm having problems with emacs.

When I use emacs inside a frame (as opposed to emacs in a terminal) the display in the buffer randomly become unresponsive.

In order to get control back, I have to use the mouse. I click on a toolbar menu item and do an action, like split the frame or open a file. After that point, the buffer becomes responsive again.

Unfortunately, I can't always use emacs in a terminal. (I'd love to, but I rely on extenstions that are broken for emacs -nw use)

I suspect that this might be a problem with emacs and gnome's compatibility.

What can I do to fix this?

---

### Post by folecr on 2010-06-02
I have this same problem. It seems to happen after some compiz operations - switch workspaces, display all workspaces, etc.

---

### Post by bobdobbs on 2010-06-03
> **folecr said:**
> I have this same problem. It seems to happen after some compiz operations - switch workspaces, display all workspaces, etc.

Yeah - I'm using compiz.

I suspected that it might be something to do with gnome. It just "felt" like a window manager issue. I guess compiz might be a cause.

---

### Post by folecr on 2010-06-14
It's not just the UI that freezes up... it looks like Emacs is waiting for an event from X that doesn't come through.

[LIST]
[*]I waited until Emacs froze up.
[*]Then ran emacsclient in a terminal
[INDENT]```
user@machine> emacsclient -nw
```[/INDENT]
[*]A blank screen showed on the emacsclient terminal
[*]When I clicked a button on the GTK emacs window, both GTK emacs and the terminal emacsclient started responding correctly.
[/LIST]

---

### Post by folecr on 2010-06-14
[https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/569914](https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/569914)

---

