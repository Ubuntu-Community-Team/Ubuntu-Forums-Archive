---
title: "Can't enable PB in Enemy-Territory"
date: 2006-04-19
forum: Gaming &amp; Leisure
---

### Post by echo $USER on 2006-04-19
I can't enable punkbuster in enemy-territory.  I installed the game and punkbuster at  /home/*****/enemy-territory but there is not a pb directory there to change the permission for pb.  Does anyone know how I can get this working?

---

### Post by Hiew on 2006-04-19
have you tried running ET with sudo?

```

sudo ./enemy-territory

```

---

### Post by echo $USER on 2006-04-19
[QUOTE=Hiew]have you tried running ET with sudo?

```

sudo ./enemy-territory

```[/QUOTE]
Thanks, i ran sudo ./et and was able to enable pb.  Thanks again.

---

### Post by romeozor on 2006-04-19
had the same thing, but all i needed to do is change the chown on the config files and stuff so i could rw them form my account

---

