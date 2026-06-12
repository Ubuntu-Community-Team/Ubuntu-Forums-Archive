---
title: "How do I remove /usr/games from my path?"
date: 2009-03-15
forum: General Help
---

### Post by MountainX on 2009-03-15
I'd like to change PATH for the whole machine. How do I do that?
```
~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

---

### Post by geirha on 2009-03-15
```
sudoedit /etc/environment
```

---

### Post by MountainX on 2009-03-15
thank you.
BTW, for other readers, the editor is a version of vi.

type "i" to insert
type ```
<ESC> :wq
``` to write changes and quit

---

### Post by MountainX on 2009-03-15
hmmm, can't seem to make the changes take effect....


```
~$ sudoedit /etc/environment 

```edited to remove /usr/games
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

LANGUAGE="en_US:en"
LANG="en_US.UTF-8"

```
saved:```
<ESC>:wq
``` 
```
~$ source /etc/environment 

```**The old path is still there**:
```
:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

---

### Post by lykwydchykyn on 2009-03-15
Did you log off and log back in?

---

### Post by geirha on 2009-03-15
If you want to use your favorite editor, set the EDITOR variable. E.g.
```
export EDITOR=nano
sudoedit /etc/environment
```

And yes, you need to log out and back in, or you can source, then export it
```
. /etc/environment
export PATH
echo $PATH
```

---

### Post by MountainX on 2009-03-15
> **geirha said:**
> If you want to use your favorite editor, set the EDITOR variable. E.g.
```
export EDITOR=nano
sudoedit /etc/environment
```And yes, you need to log out and back in, or you can source, then export it
```
. /etc/environment
export PATH
echo $PATH
```

thanks. I didn't know about the need to export. it is working now.

---

