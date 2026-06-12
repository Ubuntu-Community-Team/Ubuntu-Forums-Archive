---
title: "sudo problem"
date: 2005-12-19
forum: Desktop Environments
---

### Post by Björn on 2005-12-19
hi hi, i am using breezy and i first installed it on a little older 1.9ghrtz box and then after a couple of weeks/months on a 3.4 one.
the problem is, on the second one, the sudo command doesnt work. I don't think i am using it wrong because it worked at the first one.
When i try ```
sudo gedit
``` or anything it just makes me a new line, like this:
```
bjorn@mammas:~$ sudo gedit
Password:
bjorn@mammas:~$

```

and when i try to configure or install anything from the gnomepanel/system/administration/(anything) i am just asked for my password and then nothing happends!

if i su in terminal i can launch anything, but it is very irritating thou.
Thanks for any help. 
(can't write error messages because i never get one :P)

/Björn

---

### Post by earobinson on 2005-12-19
[http://www.ubuntuforums.org/showthread.php?t=105889&highlight=sudo](http://www.ubuntuforums.org/showthread.php?t=105889&highlight=sudo)

Let us know how it goes

---

### Post by morganth on 2005-12-19
I would assume the problem is graphics.

"sudo", you see, is for command line ... commands.

The coresponding command for graphical applications is...

[CENTER][SIZE="7"]gksudo[/SIZE][/center]
;)

---

### Post by Björn on 2005-12-20
Yey, it works perfectly! I am just ashamed that i coudn't find the thread myself:oops: 
(keywords "sudo" and "problem"/"error" is not very good ones :P)
and i guess gksudo isn't needed when you run from a terminal  ;).
A BIG thanks!

/Björn

---

