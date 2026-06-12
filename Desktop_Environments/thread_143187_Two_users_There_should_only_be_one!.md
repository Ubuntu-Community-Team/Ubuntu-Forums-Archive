---
title: "Two users? There should only be one!"
date: 2006-03-12
forum: Desktop Environments
---

### Post by Luggy on 2006-03-12
I'm getting confused by what's going on here, I should only have one user on my system but I'm getting told I have two.

```
paul@ubuntu:~$ uptime
 22:37:18 up 3 days,  3:32,  2 users,  load average: 0.74, 0.49, 0.44
paul@ubuntu:~$ sudo who
paul     :0           Mar  8 19:05
paul     pts/0        Mar  9 21:34 (:0.0)

```

When I use the Users and Groups tool in Systems->Administrations it only shows the one user.

If anyone could explain to me (or give some suggestions) as to what's going on it would be much appreciated.

---

### Post by dcstar on 2006-03-12
[QUOTE=Luggy]I'm getting confused by what's going on here, I should only have one user on my system but I'm getting told I have two.

```
paul@ubuntu:~$ uptime
 22:37:18 up 3 days,  3:32,  2 users,  load average: 0.74, 0.49, 0.44
paul@ubuntu:~$ sudo who
paul     :0           Mar  8 19:05
paul     pts/0        Mar  9 21:34 (:0.0)

```

When I use the Users and Groups tool in Systems->Administrations it only shows the one user.

If anyone could explain to me (or give some suggestions) as to what's going on it would be much appreciated.[/QUOTE]
Nothing is "going on", you have an X session and you opened a terminal to run uptime, that is two users.

---

### Post by Luggy on 2006-03-12
Doh...
[IMG]http://img.photobucket.com/albums/v190/Luggy/smiles/weary.gif[/IMG]

---

### Post by Madpilot on 2006-03-12
Try "w" instead of "uptime", it gives all of uptime's info plus a lot more, including who the users are.

---

