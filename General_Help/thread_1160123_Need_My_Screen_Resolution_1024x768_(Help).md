---
title: "Need My Screen Resolution 1024x768 (Help)"
date: 2009-05-15
forum: General Help
---

### Post by zubunto on 2009-05-15
):P Hi, I am new here and also new on ubuntu I uninstall windows xp and now i have ubuntu 9.04 updates are up to date and every thing i installd wine and install **rpg maker xp** wene i open the programe it says cant **open only with screen resolution 1024x768 or less.** and my screen resolution is 800x600 I opend dysplay and is the only option! help....

---

### Post by Ansraliant on 2009-05-15
Hi!. Have you tried to edit xorg.conf file?? I had a similar problem once.
Here's what I did:

```
$ sudo gedit /etc/X11/xorg.conf
```

Search the section Screen. Under Subsection Display add this:

```

Modes "1024x768" "800x600"

```

If you need more information, this post will help you to solve your problem.

```
http://ubuntuforums.org/showpost.php?p=129379&postcount=21
```

Good Luck!.

---

### Post by michy99 on 2009-05-15
If the post above didn't fix it, have a look at this:

[http://ubuntuforums.org/showthread.php?t=1158177](http://ubuntuforums.org/showthread.php?t=1158177)

---

### Post by zubunto on 2009-05-19
PLeaSSS nothing works

---

### Post by paradigm2 on 2009-05-19
> **zubunto said:**
> PLeaSSS nothing works

1. What video adapter do you have?

```

lspci

```

2. What monitor do you have (make and model #) ?

---

### Post by Ansraliant on 2009-05-20
Maybe you have a problem with your video driver.
What video card do you have??

---

