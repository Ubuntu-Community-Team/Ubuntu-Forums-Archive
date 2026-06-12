---
title: "File Permissoins - Isseki Nichou"
date: 2009-01-16
forum: General Help
---

### Post by Kissell on 2009-01-16
I'm constantly finding myself typing in these two commands at the command prompt.

chmod 770 * -R
chown root:users * -R

Is there a single command built-into Ubuntu/linux that I can use instead, or something in the repositories, or should I just script it for myself (i just hate to do that because then it doesn't work on every system).

I'd like a single command so I don't have to type that in twice...  something like "chopen users" or something easy that would give write full access to the users group, but anyone not in the group from even reading it.

---

### Post by blazemore on 2009-01-16
Yes you can!
Make a new text file and do this
```
#/bin/bash
chmod 770 * -R
chown root:users * -R

```

Save it as whatever you want, but make sure its easy to remember, cos that'll be the command name.
browse to where it is saved, and use the following commands
```
sudo cp **filename** /usr/bin/ -v
```
```
sudo chmod +x /usr/bin/**filename**
```

Now you can run the command at the terminal, just like any other.

---

### Post by Kissell on 2009-01-16
yeah, that's what i was gonna do...  but i was hoping there was something natively available...  cause that file won't be on every system i use...  i want it to be simplier, but I don't want to get into the habit of using commands that only exist in my own little world...

---

