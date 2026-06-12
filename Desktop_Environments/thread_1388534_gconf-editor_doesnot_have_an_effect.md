---
title: "gconf-editor doesnot have an effect"
date: 2010-01-23
forum: Desktop Environments
---

### Post by ahmetbekde on 2010-01-23
I m trying to configure panel settings with gconf-editor but although I get in with root privileges no effect can be seen.I have already read some threads about it but nothing worked. Could you please how I can see these effects? Ubuntu 9.10 Karmic

---

### Post by llawwehttam on 2010-01-23
How are you opening gconf-editor? If your run as root you will be changing things for the root not yourself.

press  Alt+F2 and type ```
gconf-editor 
``` with NO I repeat NO sudo.

---

### Post by John Bean on 2010-01-23
You beat me to it. Exactly correct answer - don't use root privileges (ever) unless you need them. In this case it's not only not needed it's completely wrong.

---

### Post by llawwehttam on 2010-01-23
> **John Bean said:**
> You beat me to it. Exactly correct answer - don't use root privileges (ever) unless you need them. In this case it's not only not needed it's completely wrong.

Just to clarify for linux NOOBs. When you run something as 'root' or using 'sudo' your are running them as the administrator using a completely separate hidden admin account. This account is hidden so you can't accidentally break things. If you don't need to never use it.

---

