---
title: "Simple for command syntax, programming?"
date: 2007-06-20
forum: Education &amp; Science
---

### Post by frojnd on 2007-06-20
I was hoping someone could give me advice or maybe exact answer for what I need. Also this isn't directly associated with ubuntu. 

I use cygwin on XP and I am trying to download content of more than one page. [http://www.odv-zb.si/odvetnik.aspx?id=](http://www.odv-zb.si/odvetnik.aspx?id=)**numbers** So there are exactly 1197 pages that I need to get their content. I tried with this two commands:

1) for i in `jot 1197 1` ; do wget http://www.odv-zb.si/odvetnik.aspx?id=$i ; done
    But there was error: HTTP request sent, awaiting response... 500 < No datra record is available. For more   information about this event, see ISA server Help. >

2) for ((i=1;i<296;i++)); dowget http://www.odv-zb.si/odvetnik.aspx?id=$i ; done
   But there was error: bash: syntax error near 'd'

---

### Post by yabbadabbadont on 2007-06-20
```
for i in $(seq 1 1197)
do
wget http://www.odv-zb.si/odvetnik.aspx?id=$i
done

```

Edit: If the $() expansion doesn't work under cygwin try
```
for i in `seq 1 1197`
```

---

### Post by frojnd on 2007-06-20
TNX :) firs one worked just fine :) and while I'm here can u give me any directions for that kinda "programming" ? tnx

---

### Post by yabbadabbadont on 2007-06-20
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)
[http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html)
[http://www.princeton.edu/~kmccarty/unixguide/](http://www.princeton.edu/~kmccarty/unixguide/)
[http://rute.2038bug.com/rute.html.gz](http://rute.2038bug.com/rute.html.gz)

---

