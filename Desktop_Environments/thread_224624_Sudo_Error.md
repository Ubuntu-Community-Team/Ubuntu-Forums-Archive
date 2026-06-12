---
title: "Sudo Error"
date: 2006-07-28
forum: Desktop Environments
---

### Post by ShAdEd_PaSt on 2006-07-28
when ever i try to use sudo i get this error... wait now it wont display an error it just doesn't work...:confused:

---

### Post by rbalfour on 2006-07-28
Are you using it like this?

$ sudo command

or

$ sudo su

which one?

---

### Post by ShAdEd_PaSt on 2006-07-29
sudo <command>
EX: sudo apt-get update

---

### Post by LKRaider on 2006-07-29
How it doesn't works?

Try typing this and post the results:
```
sudo

sudo su

sudo cat /etc/sudoers

sudo groups

groups
```

Do those commands work? Paste the outputs exaclty as you see them so we can help better.

---

### Post by ShAdEd_PaSt on 2006-07-29
> **LKRaider said:**
> How it doesn't works?

Try typing this and post the results:
```
sudo

sudo su

sudo cat /etc/sudoers

sudo groups

groups
```

Do those commands work? Paste the outputs exaclty as you see them so we can help better.
sudo- gives me all the usage
sudo su- blank (it just clears the line)
sudo cat /etc/sudoers- it says this must be edited with visudo command and a bunch of other stuff
sudo groups- only says root --bet that's the prob--
groups- ShAdEd_PaSt adm dialout cdrom etc.
p.s.(Im no noob it just got all screwed up when i fixed it for my new ati graphics card with dpkg-reconfigure xserver-xorg)--first my network broke i got that fixed now this...--

---

