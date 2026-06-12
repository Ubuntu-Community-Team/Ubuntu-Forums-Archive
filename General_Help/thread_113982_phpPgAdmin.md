---
title: "phpPgAdmin"
date: 2006-01-07
forum: General Help
---

### Post by rensu on 2006-01-07
Can anyone tell me why i can't login with other users from web? Only with first user what i created i can login. Trying to create with phpPgAdmin new user and trying to login with the name and it says Login failed.

---

### Post by Ces on 2006-01-08
(I am using this thread in stead of starting another. Hope it is okay.)

I am not able to login at all with phpPgAdmin.

I have (re)installed:
apache2 [COLOR="Green"]&#8592; works[/COLOR]
php5 [COLOR="Green"]&#8592; works[/COLOR]
postgresql-8.0 [COLOR="Green"]&#8592; works[/COLOR]
phppgadmin [COLOR="Red"]&#8592; fails[/COLOR]

At first I couldn't even access phppgadmin but then I made a link ([FONT="Courier New]sudo ln -s /usr/share/phppgadmin /var/www/phppgadmin[/FONT]) and now I get the log-in screen at least. Though I can not log in. Have created a user and given a password.

Anyone knows what I've failed to  (I've tried looking for help in the forums and the wiki, but nothing helped.)

```
kess@ardhanari:/$ sudo less /var/log/postgresql/postgresql-8.0-main.log | tail -n 1
FATALT:  Ident authentication failed for user "kess"

```

```
kess@ardhanari:/$ sudo less /etc/postgresql/8.0/main/pg_hba.conf | tail -n 8
# TYPE  DATABASE    USER        CIDR-ADDRESS          METHOD

# "local" is for Unix domain socket connections only
local   all         all                               ident sameuser
# IPv4 local connections:
host    all         all         127.0.0.1/32          md5
# IPv6 local connections:
host    all         all         ::1/128               md5

```

---

### Post by rensu on 2006-01-08
Same problem as mine:confused:

---

### Post by rensu on 2006-01-09
Found the problem. You just have to edit the /etc/postgresql/8.0/main/pg_hba.conf
There add few lines:
> local all postgres ident sameuser
> local all all password
And commented the line:
#local   all         all                               ident sameuser 
That worked for me. Now i can login with any user I want:rolleyes:

---

### Post by Ces on 2006-01-09
Hooray!! It works like a charm now. Thanks! :D

---

