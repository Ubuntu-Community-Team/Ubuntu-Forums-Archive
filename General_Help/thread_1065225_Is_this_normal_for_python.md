---
title: "Is this normal for python?"
date: 2009-02-09
forum: General Help
---

### Post by paldives on 2009-02-09
Is it normal to have about 10 python processes in system monitor?

---

### Post by chronographer on 2009-02-09
I only have 1

---

### Post by snova on 2009-02-09
It depends on what you are doing. Python is a programming language, so if you see it in the System Monitor, it means that there is a program running somewhere that is written in Python.

It could be a number of things. If you look at the Command Line, it should give you an idea of what program is actually running.

---

### Post by paldives on 2009-02-09
It has nine of them open when I start up ubuntu.  and when I press end process it just stays and does not stop.  I seems like it is slowing my computer down also because some of them show as running at 5-21 MiB while other apps run around in the 100s KiB except for firefox which runs at 120Mib but I believe that is normal from what I remember from windows.

---

### Post by Atzu on 2009-02-09
check what u run at startup (System->Preference->Sessions) look if there's something weird there... if you don't know what are they post them here.


Edit: On system monitor you can also go to view and check "Dependencies" and you can see what are python dependencies(dunno how to type that :/) maybe programs running

---

### Post by paldives on 2009-02-10
Thank you very much I managed to find out that two of them were programs I did not need at startup while the other 4 or so were plug ins for AWN and Screenlets

---

