---
title: "CD repository"
date: 2006-01-07
forum: General Help
---

### Post by randal on 2006-01-07
When I was using Ubuntu, referring to Kubuntu CD for packages was very easy. When I insert the CD, the system would recognize it. But Kubuntu, doesn't seem to work like that. How do I make Kubuntu to work like that?

[SIZE="2"]I don't have net connection on my Linux so I don't have any way to access the online repo.[/SIZE]

---

### Post by aysiu on 2006-01-07
What does your /etc/apt/sources.list look like?

---

### Post by randal on 2006-01-09
I have all repo locations commented except for the one which refers to Kubuntu CD.

---

### Post by randal on 2006-01-13
Please help.

---

### Post by Freddy on 2006-01-13
You can add a new cd with the command.
```
sudo apt-cdrom add
```
So plugin your install cd and hit it.

/// Freddan

---

