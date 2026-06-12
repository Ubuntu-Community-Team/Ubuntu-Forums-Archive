---
title: "Shell script to show my external ( public ) IP - anyone ?"
date: 2009-06-01
forum: General Help
---

### Post by ActiveFrost on 2009-06-01
I'm behind a router and I would like to see my external ( public ) IP inside my computer ( Shell script, Python .. ), without opening my routers admin panel or going to websites which could detect it.
Maybe someone knows, is it possible or I'm looking for something that does not exist ?

---

### Post by adrianx on 2009-06-01
You could use wget
```
wget -qO - http://www.whatismyip.org
```

---

### Post by nebileix on 2009-06-01
Create a dynamic dns account with [http://www.dyndns.com]("http://www.dyndns.com").

use these command to get your current ip address.

```
$ dig [yourregisteredwebsitewithdyndns] +short
```

You could do bash script to echo the ip address or as argument.

---

### Post by ActiveFrost on 2009-06-01
> **adrianx said:**
> You could use wget
```
wget -qO - http://www.whatismyip.org
```

It does nothing ( no output, no files .. ) !

> **nebileix said:**
> Create a dynamic dns account with [http://www.dyndns.com]("http://www.dyndns.com").

use these command to get your current ip address.

```
$ dig [yourregisteredwebsitewithdyndns] +short
```

You could do bash script to echo the ip address or as argument.

Thanks - I completely forgot about DNS ! In that case, no need to use big shell scripts - ping command will show my IP :)

---

### Post by adrianx on 2009-06-01
> **ActiveFrost said:**
> It does nothing ( no output, no files .. ) !
Oh, that's strange. It works for me. :confused:
When I do it, I get:
adrian@quartz:~$ wget -qO - [http://www.whatismyip.org](http://www.whatismyip.org)
[COLOR=Navy]41.xxx.xxx.xxx[/COLOR]adrian@quartz:~$

There is no line break, but in a script you would probably assign the value to a variable, or could say echo `wget -qO - http://www.whatismyip.org`

---

### Post by nebileix on 2009-06-01
> Thanks - I completely forgot about DNS ! In that case, no need to use big shell scripts - ping command will show my IP :)

Yeah ping will do the job. Will be easier to use dig if u are scripting it.

---

### Post by ActiveFrost on 2009-06-01
> **nebileix said:**
> Yeah ping will do the job. Will be easier to use dig if u are scripting it.

Not sure about what dig does, but if you say so .. will take a look at it ;)

---

### Post by nebileix on 2009-06-01
Try

```
dig www.yahoo.com +short
```

you'll just get the ip address only.

---

### Post by ActiveFrost on 2009-06-01
> **nebileix said:**
> Try

```
dig www.yahoo.com +short
```

you'll just get the ip address only.

Not really .. I got more than just an IP address :
```
dainis@suncore:~$ dig www.yahoo.com +short
www.wa1.b.yahoo.com.
www-real.wa1.b.yahoo.com.
87.248.113.14
```

---

### Post by nebileix on 2009-06-01
> **ActiveFrost said:**
> Not really .. I got more than just an IP address :
```
dainis@suncore:~$ dig www.yahoo.com +short
www.wa1.b.yahoo.com.
www-real.wa1.b.yahoo.com.
87.248.113.14
```

oopss.. my bad. I use it for my ddns and only got the ip. :p

---

### Post by nebileix on 2009-06-01
> **ActiveFrost said:**
> Not really .. I got more than just an IP address :
```
dainis@suncore:~$ dig www.yahoo.com +short
www.wa1.b.yahoo.com.
www-real.wa1.b.yahoo.com.
87.248.113.14
```

Try filtering it with grep.

```
dig www.yahoo.com +short | grep '^[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}$'
```

---

### Post by ActiveFrost on 2009-06-01
> **nebileix said:**
> Try filtering it with grep.

```
dig www.yahoo.com +short | grep '^[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}$'
```

Thank you - works like a charm ;)

---

### Post by KodieG on 2010-03-25
> **adrianx said:**
> You could use wget
```
wget -qO - http://www.whatismyip.org
```

wget -qO- whatismyip.org && echo

add && echo at the end and you'll get your line break. looks alot better.

---

### Post by adrianx on 2010-03-25
I have found a quicker site (and they add a line break). :)
```
wget -qO - icanhazip.com
```

---

