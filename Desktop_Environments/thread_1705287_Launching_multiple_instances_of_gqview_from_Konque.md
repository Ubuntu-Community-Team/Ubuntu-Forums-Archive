---
title: "Launching multiple instances of gqview from Konqueror"
date: 2011-03-12
forum: Desktop Environments
---

### Post by fixitdude on 2011-03-12
Someone asked....

"When I try to launch multiple instances of certain applications from either the quick launch buttons on the kicker, or through the KDE menu, the second instance fails to launch, and I get a spinning hour-glass icon on the task list section of the kicker. Yet, if I launch multiple instances from the shell, they start up fine. Why does KDE not allow me to do this, and how can I fix it so I can? It allows me to open multiple konsoles or gVim instances, but not gqview for example. It is extremely frustrating."

But it was never answered.

One thing that frustrated me was that when clicking on a jpg file from Konqueror, gqview used to open multiple instances for each pic, now it doesn't since upgrading ubuntu.

The solve for this was to right click on a jpg file, Properties, then (not obvious) click on that little icon with a wrench in it to "edit file type", then click on GQview and hit the "edit button".

If you got that far, you want the tab "Application" and now edit the command to read ONLY "gqview %F".

It was "gqview -r %F", don't ask me why because gqview doesn't have a "-r" option if you look at the man page.

So maybe it's not a kicker problem but a "Command" problem so go look at the other programs you want to do the same with and maybe this will fix it.

---

