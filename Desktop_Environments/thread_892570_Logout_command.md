---
title: "Logout command"
date: 2008-08-17
forum: Desktop Environments
---

### Post by zephyrus17 on 2008-08-17
What's the command I can type into the terminal that's the same as CTRL+ALT+BACKSPACE?

I've tried ```
gnome-session-save --kill --silent
```but that just saves the session and restarts.

---

### Post by mali2297 on 2008-08-17
Try
```

sudo /etc/init.d/gdm restart

```

---

### Post by zephyrus17 on 2008-08-17
Oh, sorry, I forgot to mention that I'm trying to do this from the Openbox right click menu. It didn't work, by the way.

---

### Post by eriqjaffe on 2008-08-17
I think you're thinking of ```
openbox --exit
```

---

### Post by zephyrus17 on 2008-08-17
Nope. It doesn't work. That's just the same. It just reloads openbox

---

