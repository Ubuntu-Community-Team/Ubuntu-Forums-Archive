---
title: "Fails to go into stand by?"
date: 2008-12-18
forum: General Help
---

### Post by amdalex on 2008-12-18
I set my computer to go to sleep after 45 minutes of inactivity and then I went to bed. When I woke up this morning my computer was off. I turned it on and it said something about a failure to suspend. I have Ubuntu 8.10 and my system specs are in my sig. How can I fix this.

---

### Post by amdalex on 2008-12-18
Does anyone know what might have caused this?

---

### Post by amdalex on 2008-12-19
bump

---

### Post by amdalex on 2008-12-20
bump

---

### Post by amdalex on 2008-12-22
bump

---

### Post by amdalex on 2008-12-23
bump

---

### Post by kerry_s on 2008-12-23
try running it from the command line to see what it says.
i'm not sure what you have installed to suspend.

sudo s2ram
sudo s2ram -f
sudo pm-suspend

there's a lot of options for pm-suspend use "man pm-suspend" to see them.

---

### Post by frenchn00b on 2008-12-23
by the way , have you got installed : 
apmd (old pc)
or acpid 
?
(taht turns off auto the pc & do more )

---

