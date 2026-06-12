---
title: "No windows borders using compiz"
date: 2010-04-17
forum: Desktop Environments
---

### Post by mfnano on 2010-04-17
hi,

I installed ubuntu 10.04 and after installing the drivers for my graphic card ATI Mobility Radeon HD4570, windows borders do not appear anymore.

When I type "metacity --replace" borders come back, but I can't use compiz, also when I try to disable "Window Decoration" from the compizConfig Settings it doesn't work, it keeps always enabled.

I tried this hack here [http://ubuntuforums.org/showthread.php?t=537588]("http://ubuntuforums.org/showthread.php?t=537588") but it didn't work for me (or I didn't apply it correctly, I'm new to the system).

Thank you.

---

### Post by ender4 on 2010-04-17
I had a similar problem.  Typing```
emerald --replace
``` fixed the problem temporarily.  And if I remember correctly, I needed to changes some setting to start up emerald on login.

---

### Post by mfnano on 2010-04-17
> **ender4 said:**
> I had a similar problem.  Typing```
emerald --replace
``` fixed the problem temporarily.  And if I remember correctly, I needed to changes some setting to start up emerald on login.

Well it's kinda work, but the theme is not really a good one, can't I just restore the borders back with the current (default) theme?

---

### Post by micio on 2010-04-19
Install compiz-configurator (or something similar) and add window decoration plugin

---

### Post by mfnano on 2010-04-19
> **micio said:**
> Install compiz-configurator (or something similar) and add window decoration plugin

Actually I did so, but it didn't work.

What worked for me is that I installed the **Simple CompizConfig Settings Manager** and changed the profile from **Default** to **Advanced** and it worked!! :)

---

### Post by andrea000 on 2010-04-20
Open ccsm and go to the workarounds plug in and
check legacy full screen support reboot and see
if that fixes your borders.

---

### Post by ptrinder64 on 2010-05-02
A suggestion here, if you go to Compiz have you selected the Windows Decoration option? If the answer is 'yes', go into the Compiz Windows Decoration settings and enter the following in the 'Command' field: 

```

/usr/bin/compiz-decorator

```

and restart. Hopefully this will sort it as it did for me. 

Let us know if it works.

---

