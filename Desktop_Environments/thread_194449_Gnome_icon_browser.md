---
title: "Gnome icon browser??"
date: 2006-06-11
forum: Desktop Environments
---

### Post by tchock on 2006-06-11
Is it just me? I have a lot of problems w/ the gnome icon browser when attempting to select icons for shortcuts on the menu & panel. Half the time the icon browser will just close itself immediately after clicking "No icon" to open the browser.

If it does open, the only way to find icons is by browsing manually -- if I type anything into the address bar (e.g. /o, on my way to typing /opt... for example) it will crash on the o.

These little things are really breaking my will.

---

### Post by CronoDekar on 2006-06-11
I had that happen to me too when trying to select an icon for a Swiftfox shortcut the other day.  I think it's a bug -- try logging out and logging back in, or restarting X (Ctrl-Alt-Backspace, which will also log you out.)

I just filed a bug report here (which I should've done when it happened, but I didn't think of it):
[https://launchpad.net/distros/ubuntu/+bug/49384](https://launchpad.net/distros/ubuntu/+bug/49384)

If you can confirm it and give any further info, that'd be great.

---

### Post by jvictor on 2006-06-11
To add on, I think we need to be able to type in the location instead of that uneditable thing .. its so frustrating to use it ! I read somehwere how to disable it but cant jsut find that post now.

---

### Post by temcat on 2006-06-12
This is a known bug, I reported it too and got a reference to the corresponding upstream bug from a dev:

[http://bugzilla.gnome.org/show_bug.cgi?id=310288#c10](http://bugzilla.gnome.org/show_bug.cgi?id=310288#c10)

---

### Post by CronoDekar on 2006-06-12
[QUOTE=temcat]This is a known bug, I reported it too and got a reference to the corresponding upstream bug from a dev:

[http://bugzilla.gnome.org/show_bug.cgi?id=310288#c10](http://bugzilla.gnome.org/show_bug.cgi?id=310288#c10)[/QUOTE]

I found that when searching to see if already posted, but it doesn't quite look like the same problem.  In that bug the icons turn gray and can't be selected; in our bug the icon browser closes instantly once it's opened, before even getting to choose the folder.

Though of course, they may be related.  It seems like the icon browser just needs an overhaul :)

---

