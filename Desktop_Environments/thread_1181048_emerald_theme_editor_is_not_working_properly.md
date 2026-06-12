---
title: "emerald theme editor is not working properly"
date: 2009-06-07
forum: Desktop Environments
---

### Post by jishnu on 2009-06-07
my emerald theme editor is not working properly.when i use the command emerald --replace theme gets active but it is temporary only it changes to earlier state when i close the terminal help me

---

### Post by oldos2er on 2009-06-07
Emerald requires compiz running as window manager. Are you running compiz?

---

### Post by overdrank on 2009-06-07
> **jishnu said:**
> my emerald theme editor is not working properly.when i use the command emerald --replace theme gets active but it is temporary only it changes to earlier state when i close the terminal help me

When you close the terminal you kill the process. Use the alt, F2 and enter the command.

---

### Post by jishnu on 2011-06-28
thank you

---

### Post by mcduck on 2011-06-28
...actually if you want to use Emerald as your window decorator permanently (as opposed to running it only when you specifically execute it yourself from a terminal) you need to configure it in the Compiz settings.

Just open CompizConfig Settings Manager (install it if you haven't got it already), then browse into "Window Decoration"-plugin's settings and set the "Command" to "/usr/bin/emerald". After that Compiz will use Emerald as it's default decorator.

---

