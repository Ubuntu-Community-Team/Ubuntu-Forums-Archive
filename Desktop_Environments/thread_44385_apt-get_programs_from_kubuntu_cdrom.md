---
title: "apt-get programs from kubuntu cdrom"
date: 2005-06-25
forum: Desktop Environments
---

### Post by mortram on 2005-06-25
I have a Kubuntu cd, but am happy with my Ubuntu desktop.  However, I am a modem user and want to get K3b and the needed libs w/o having to wait for a long download, and I know they're on the disk I have.  

Is there a way I can apt-get a specific program, namely K3b, from my Kubuntu disc?

Gnomebaker's got potential but it doesn't burn DVD-Video or handle mp3-to-audio cd conversion very well.

---

### Post by SGC on 2005-06-25
Try the following, first run this command form the terminal:

```

apt-cdrom add

```
Insert kubuntu CD and press enter

Then update the repositories list to include kubuntu CD:
```

apt-get update

```

Finally, install k3b:
```

apt-get install k3b

```

---

### Post by mortram on 2005-06-26
excellent, thanks very much!

---

