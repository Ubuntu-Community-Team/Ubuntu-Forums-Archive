---
title: "Refresh Rate - changing xorg.conf"
date: 2005-04-14
forum: Desktop Environments
---

### Post by HeXetic on 2005-04-14
Well I installed Ubuntu and the refresh rate is at 60Hz and there isn't any other options for it. So I came here and apparently you have to change it in the xorg.conf file the problem is I can't write to this file. Can some body help me before my eyes burn out  :sad:

---

### Post by Stormy Eyes on 2005-04-14
[QUOTE=HeXetic]Well I installed Ubuntu and the refresh rate is at 60Hz and there isn't any other options for it. So I came here and apparently you have to change it in the xorg.conf file the problem is I can't write to this file. Can some body help me before my eyes burn out  :sad:[/QUOTE]

Why can't you write to it? Post the output of **ls -al /etc/X11/xorg.conf**, please. It might be that you just have to do **sudo $EDITOR /etc/X11/xorg.conf**.

---

### Post by HeXetic on 2005-04-14
ok after typing in 

```
ls -al /etc/X11/xorg.conf
``` I get 

```
-rwxrwxrwx  1 root root 3122 2005-04-13 00:01 /etc/X11/xorg.conf
```

---

### Post by Stormy Eyes on 2005-04-14
OK. Can you save changes to /etc/X11/xorg.conf if you do **sudo gedit /etc/X11/xorg.conf**? Since the file is owned by root, you have to be root to alter it.

---

### Post by HeXetic on 2005-04-14
It worked!!! Thanks for that looks so much better.  \\:D/

---

### Post by Stormy Eyes on 2005-04-14
[QUOTE=HeXetic]It worked!!! Thanks for that looks so much better.  \\:D/[/QUOTE]

No problem. Just keep in mind that you have to use sudo to edit config files that don't live in your $HOME.

---

