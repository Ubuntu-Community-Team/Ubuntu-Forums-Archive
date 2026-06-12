---
title: "gnome theme doesn't work"
date: 2006-10-27
forum: Desktop Environments
---

### Post by meiclamo on 2006-10-27
hi.

i updated my ubuntu from dapper to edgy-eft 6.10 yesterday.

everything seemed to be fine, but i just found that theme configuration does not work.

in detail, i wanna change my theme to "Human", and i choose it in the theme  configuration window. my desktop doesn't change at all, however. the other themes doesn't change my desktop, too.

i reinstalled "gnome-theme" in the synaptic, but still out of order!!

anyone knows solutions?

---

### Post by skyfisher on 2006-10-27
You probably should load gnome-settings-daemon manually.

---

### Post by meiclamo on 2006-10-27
how can i do that?

thank you for your advice :)

---

### Post by meiclamo on 2006-10-27
i got it.

i manually started gnome-settings-daemon, and everything works well.

thank you.

---

### Post by frozen5555 on 2006-10-27
thanks i was also having the same problem.

---

### Post by ds500ss on 2006-11-12
move your settings

mkdir dotfiles

mv .* dotfiles/.
login again

it will work!

---

