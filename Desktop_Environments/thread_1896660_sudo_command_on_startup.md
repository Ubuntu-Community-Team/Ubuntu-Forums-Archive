---
title: "sudo command on startup"
date: 2011-12-17
forum: Desktop Environments
---

### Post by The Khra on 2011-12-17
Hi,
I want to automount a truecrypt partition at lubuntu startup (using keyfiles) without a prompt for sudo password. I tried to put the truecrypt mount command in /etc/rc.local but it doesen't worked. I also added the command to /etc/xdglxsession/Lubuntu/autostart but no way. How can I do that?
Thanks in advance
The Khra

---

### Post by boast on 2011-12-17
rc.local runs things as root

---

### Post by 9072997 on 2011-12-17
i think, though i am not positive that you have to soft link things in rc.local to /etc/rc5.d/S99procesName to get them to start in runlevel 5 (the default runlevel)

---

### Post by The Khra on 2011-12-17
> **boast said:**
> rc.local runs things as root
As said this does not work for me
[QUOTE=9072997]i think, though i am not positive that you have to soft link things in  rc.local to /etc/rc5.d/S99procesName to get them to start in runlevel 5  (the default runlevel)[/QUOTE]
What should I put in /etc/rc5.d? A bash file including the command?

---

### Post by dentaku65 on 2011-12-17
You can do it in this (UNSAFE) way.

```
nano $HOME/pass
```
and write your password in this file.

Then, load the command:
```
sudo *your_command* < $HOME/pass
```

But, rc.local must works in this way:
```
sudo chmod +x /etc/rc.local
```
And the file must end always with this string:
> exit 0


Enjoy

---

