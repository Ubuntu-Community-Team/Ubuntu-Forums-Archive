---
title: "Run command on X (or kdm) startup"
date: 2005-04-23
forum: Desktop Environments
---

### Post by Seth on 2005-04-23
I've been running Ubuntu for quite some time and had my multimedia keys working great. Under KDE, I had to make a custom xmodmap file and then run

**xmodmap /etc/xmodmap.conf**

to get my keys to work. Where do I put this command to get it to run either when KDM or X starts? Thanks.

---

### Post by Xerampelinae on 2005-04-24
Perhaps in ~/.xsession

This man page seems relevant...
```
man X
```

---

### Post by Seth on 2005-04-24
Thank you for the suggestion. I placed that command in ~/.xsession (which didn't exist, so I created it), but nothing happened.

---

### Post by cwaldbieser on 2005-04-24
Could you just put it under ~/.kde/Autostart?  It wouldn't run until you actually started your kde session, though.

---

### Post by Seth on 2005-04-24
[QUOTE=cwaldbieser]Could you just put it under ~/.kde/Autostart?  It wouldn't run until you actually started your kde session, though.[/QUOTE]
 I actually tried that originally but it just opened the file in Kate for text editing :-S

---

### Post by windymiller on 2005-04-25
[QUOTE=Seth]I actually tried that originally but it just opened the file in Kate for text editing :-S[/QUOTE]
 make sure you have "#!/bin/bash" as the first line of the file (without the quotes)

---

### Post by Xerampelinae on 2005-04-25
Maybe your files aren't executable?

```

chmod +x ~/.xsession

```

The same is probably true for the other file mentioned above..

---

### Post by Seth on 2005-04-25
[QUOTE=windymiller]make sure you have "#!/bin/bash" as the first line of the file (without the quotes)[/QUOTE]
 Thanks, worked perfectly. Wasn't too familiar with shell scripts but now I'm all read up.

(CHMOD'ing .xsession didn't work)

---

