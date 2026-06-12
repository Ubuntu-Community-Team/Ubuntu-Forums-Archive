---
title: "Where does the login shell go when X starts?"
date: 2008-02-11
forum: Desktop Environments
---

### Post by B-Con on 2008-02-11
When I originally login to my machine and start X, what happens to my login shell? Should X be running from a login shell, or does it get closed once X starts? If I open a terminal and do "w", I only see the pts/1 that that shell is on.

---

### Post by Zed on 2008-02-11
If you look in /etc/event.d you'll see six files, tty1 to tty6. Each of these runs getty to start a tty. When you're not starting X by default, you start in tty1.

You can get back to your original tty with Ctrl-Alt-F1 (and so on through Ctrl-Alt-F6.) Ctrl-Alt-F7 will take you back to X.

---

### Post by B-Con on 2008-02-11
OK, I see. What happens if I do start X automatically?

---

### Post by Glowing Fish on 2008-02-11
Also, you can use Ctrl-Alt-F2 through Ctrl-Alt-F6 (or up, depending on configuration)
to get another virtual terminal. Remember this, it will come in handy!

---

### Post by Zed on 2008-02-11
If your system's configured to start X, then ttys 1-6 still exist, you just won't be logged into any of them. if you go to one of them, you'll get a login prompt.

---

