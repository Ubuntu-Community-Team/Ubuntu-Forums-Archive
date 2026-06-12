---
title: "Simple redirection Question"
date: 2006-06-25
forum: Desktop Environments
---

### Post by Thund3rstruck on 2006-06-25
Ok suppose I wanted to run deborphan but redirect the output into the apt-get remove command (with a silent switch). How exactly could I acheive this?

deborphan > sudo apt-get remove %1

or something like that??

TIA,
T3

---

### Post by Thund3rstruck on 2006-06-25
Anyone?

It seems like a simple question...

---

### Post by Thund3rstruck on 2006-06-25
ok... so I guess its not possible then. I was hoping to do it in one command.

here's a script tp do it

```

#/bin/bash
fileName="/tmp/orphans.txt"
deborphan > $fileName
while read line
do
	sudo apt-get -y remove "$line" 
done < $fileName

```

---

### Post by Thund3rstruck on 2006-06-28
Additionally, I have just read that you can use the backtick character to send the results of one command into another command (sounds like the SQL IN syntax).

sudo apt-get -y remove `deborphan`

---

### Post by harisund on 2006-06-28
```
deborphan | xargs sudo apt-get -y --purge remove
```

I have this in my ~/.bash_logout so that it gets executed every time I log out of the machine (I always login remotely into this server using SSH :) )

---

