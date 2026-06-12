---
title: "Emerald Problem"
date: 2010-02-08
forum: Desktop Environments
---

### Post by maddy_in65 on 2010-02-08
I have tried to add "emerald --replace" in startup application but it is not every time when i startup system again. I have to run the command again. How do i run it at startup.

---

### Post by lovinglinux on 2010-02-08
Open "System >> Preferences >> Startup Applications" and add "emerald --replace" command to the list.

---

### Post by mcduck on 2010-02-08
The best way is to sdirectly tell Compiz to sue Emerald as it's window decorator. Just install CompiCOnfig Settings Manager (if you ahven't already don that), then go to Window Decorations -plugin and change the "Command"-field to "/usr/bin/emerald".

This way you'll be loading Ememrald in the firat place, instead of first loading soem other window decorator and then replacing that with Emerald (like you do if you just add "emerald --replace" to your startup commands).

---

### Post by lovinglinux on 2010-02-08
> **mcduck said:**
> The best way is to sdirectly tell Compiz to sue Emerald as it's window decorator. Just install CompiCOnfig Settings Manager (if you ahven't already don that), then go to Window Decorations -plugin and change the "Command"-field to "/usr/bin/emerald".

This way you'll be loading Ememrald in the firat place, instead of first loading soem other window decorator and then replacing that with Emerald (like you do if you just add "emerald --replace" to your startup commands).

Yep, that's a better way. I forgot about it, since I don't change my Compiz settings for months. In fact I use that too.

---

