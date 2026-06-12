---
title: "Gnome problems"
date: 2009-01-06
forum: Desktop Environments
---

### Post by HeroXx on 2009-01-06
Hiya!

I am trying to run srcds under gnome through a launch shortcut that runs the command xterm -e cd /home/administrator/css1 however when I run that command it will give an error:

xterm: cannot execvp cd: No such file or directory

Then when I run cd /home/administrator/css1 in that same window it will work...

---

### Post by blazemore on 2009-01-06
```
xterm -e "cd /home/administrator/css1"
```

---

### Post by HeroXx on 2009-01-07
When I set that it just flashes up and disappears :S

---

### Post by blazemore on 2009-01-07
```
xterm -e "cd /home/administrator/css1 &&"
```

---

### Post by HeroXx on 2009-01-07
Same result.

---

### Post by HeroXx on 2009-01-07
Anyone?

---

### Post by blazemore on 2009-01-08
Why don't you use gnome-terminal instead of xterm?
```
gnome-terminal -e "cd /home/administrator/css1 &&"
```

---

### Post by HeroXx on 2009-01-11
This gives a strange problem:

[IMG]http://www.rush-gaming.co.uk/wtf.jpg[/IMG]

---

### Post by HeroXx on 2009-01-11
Help :(

---

### Post by tonytr on 2009-01-12
How about something like this:

```
xterm -e "cd /tmp; /bin/bash" &
```

---

### Post by HeroXx on 2009-01-13
xterm: cannot execvp cd: No such file or directory

---

### Post by tonytr on 2009-01-13
Very odd. "cd" is a built-in utility in the shell. What is your default shell?

Does this work or produce a similar error?
```
xterm -e "pwd ; /bin/bash" &
```

---

### Post by HeroXx on 2009-01-14
xterm: Can't execvp pwd ; /bin/bash: No such file or directory

---

### Post by HeroXx on 2009-01-15
Bump

---

### Post by HeroXx on 2009-01-15
:(

---

### Post by HeroXx on 2009-01-16
No-one has had this problem before?

---

### Post by HeroXx on 2009-01-18
Still bumping, anyone know anywhere else to look for help?

---

