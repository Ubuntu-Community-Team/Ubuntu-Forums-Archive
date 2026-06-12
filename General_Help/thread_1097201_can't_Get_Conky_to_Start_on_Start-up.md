---
title: "can't Get Conky to Start on Start-up"
date: 2009-03-15
forum: General Help
---

### Post by orc_dragoon on 2009-03-15
I did the .conky_start.sh

with

```
#!/bin/bash
sleep 20 && conky
```

I put this in my home file

example:

```
/home/josh/
```

I put it in sessions.

Am I doing something wrong?

---

### Post by dje on 2009-03-15
did you set executable permissions on the script?
```
chmod +x /home/josh/.conky_start.sh
```

hope that helps,
dje

---

### Post by orc_dragoon on 2009-03-15
> **dje said:**
> did you set executable permissions on the script?
```
chmod +x /home/josh/.conky_start.sh
```

hope that helps,
dje

Didnt work.

---

### Post by dje on 2009-03-15
can you post what you put in sessions?

---

### Post by orc_dragoon on 2009-03-15
```


name:Conky start
Command: /home/josh/.conky_start.sh

```

---

### Post by dje on 2009-03-15
ok since the script is not in your [PATH]("http://www.linuxcommand.org/wss0010.php#path") you must make a small change:
```

name:Conky start
Command: /home/josh/[COLOR="Red"]./[/COLOR].conky_start.sh

```

dje

---

### Post by orc_dragoon on 2009-03-15
Didnt work.

---

### Post by dje on 2009-03-15
can you run the command from the terminal and see if it works?
if it doesn't work can you post any output here

dje

---

### Post by orc_dragoon on 2009-03-15
It worked in terminal and here was output.

```

josh@ubuntu:~$ /home/josh/./.conky_start.sh
Conky: /home/josh/.conkyrc: 13: config file error
Conky: desktop window (4e) is root window
Conky: drawing to desktop window
Conky: drawing to double buffer
```

---

### Post by orc_dragoon on 2009-03-15
bump.

---

### Post by bekind2thenoob on 2009-03-15
Try ```
sh ./.conky_start.sh
``` in sessions

---

### Post by orc_dragoon on 2009-03-15
no worky

---

### Post by jjgomera on 2009-03-16
if you are using xubuntu and only a conky instance, why dont you add to session simply conky

---

### Post by orc_dragoon on 2009-03-16
already tried that.

---

### Post by jonobr on 2009-03-16
just for giggles I gave this thing a try.

Im on ubuntu Ibex, 
I created a file in my home directory and called it something.
I just put conky in the file,
I placed it in sessions, and rebooted.

Didnt work.
I did a 

```
chmod 777 filename
``` 
rebooted 
and conky came up on boot up.

MAkes me think either their a difference between ubuntu and you version of xubuntu
or
theres a permissions issue?
or 
what your using to start it is wrong. Which is unlikely as your tried using the command line,
or

Im just lucky:-)

PS- of course 777 is not the best permission to set.

---

