---
title: "Activities on 20.04 do not suggest software but works on 19.10"
date: 2020-04-24
forum: Desktop Environments
---

### Post by vitalio on 2020-04-24
Hello

I've just upgraded to focal and noticed odd thing. Activities in gnome-shell do not suggest not installed software. For example typing "irc" on 19.10 will suggest Polari along some other IRC clients, but on 20.10 will yeild empty result after 1 min of searching.

I've attached 2 screenshots

Is it normal? Bug?

---

### Post by Dennis N on 2020-04-24
Probably not normal because I get suggested things to install. See screenshot attached.

---

### Post by vitalio on 2020-04-24
Then question is how gnome-shell works and where from it gets its suggestions? :-k Maybe has to do with the fact that 20.10 is recent and I'm in Romania

---

### Post by Dennis N on 2020-04-24
I don't know if this explains why mine works, but I removed Ubuntu Software (Snap Store) and installed Gnome Software from the Ubuntu Repository. Possibly the search works better with that?

---

### Post by vitalio on 2020-04-24
How exactly you did that, please? like there is a package gnome-sofware ?

---

### Post by Dennis N on 2020-04-24
> **vitalio said:**
> How exactly you did that, please? like there is a package gnome-sofware ?

Use terminal:

```
snap remove snap-store
```

Then,

```
sudo apt install gnome-software
```

---

### Post by vitalio on 2020-04-24
Apparently my search is weird.

---

### Post by vitalio on 2020-04-24
Thanks, installing gnome-software worked.

---

### Post by Dennis N on 2020-04-24
> **vitalio said:**
> Apparently my search is weird.

Very interesting to see that Ubuntu Software (Snap Store) isn't listed in the search settings! I'm glad to hear that the switch to Gnome Software fixed the problem.

---

### Post by vitalio on 2020-04-24
Yes very strange. Canonical pushing for snap but not integrating it to GNOME Shell. Go figure ¯\_( &#865;&#10075;&#8239;&#860;&#662; &#865;&#10075;)_/¯

---

