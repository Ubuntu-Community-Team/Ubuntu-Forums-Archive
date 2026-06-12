---
title: "Fluxbox startup"
date: 2009-06-06
forum: General Help
---

### Post by akernan on 2009-06-06
I use Fluxbox on Ubuntu but my startup file is not running.  I have a few commands added to my startup file but they are not running.

Is there a notification tray for Fluxbox?  I have some appts in Evolution that I need to be notified of.

Can anyone help me?

---

### Post by sdennie on 2009-06-06
What file are you adding your commands to?  Also, yes, there is a notification tray in fluxbox.  It should be added to the toolbar by default but, you can check in ~/.fluxbox/init and make sure it has the systemtray option in session.screen0.toolbar.tools.

---

### Post by akernan on 2009-06-06
idesk &
evolution-alarm-notify &

When I login to Fluxbox, the idesk command is not run.

Thanks,
Tony

---

### Post by akernan on 2009-06-07
Can anybody help me with the startup file?

---

### Post by akernan on 2009-06-07
Nevermind.  I just had to read the Fluxbox wiki again.

---

