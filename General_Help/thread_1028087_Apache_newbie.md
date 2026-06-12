---
title: "Apache newbie"
date: 2009-01-02
forum: General Help
---

### Post by d4rk5h4dow5 on 2009-01-02
OK so I want to setup my web server but I'm a complete noobatron with all this lol  (still learning everyday :D   )

Apache Is installed and I already registered with no-ip but I don't know what to do next.. can someone point me in the right direction. I just need to know where to drop my files for my site and how to make apache serve that out.

I know it's kinda vague but I'm not sure where to go from this point.

-Thanks for all the help

also I thought I should add what it shows me when I do ps (don't know if this helps)

root     19928  0.0  0.2  13144   488 ?        Ss   19:54   0:00 /usr/sbin/apache2 -k start
www-data 19930  0.0  0.1  13276   372 ?        S    19:54   0:00 /usr/sbin/apache2 -k start
www-data 19934  0.0  0.1  13276   372 ?        S    19:54   0:00 /usr/sbin/apache2 -k start
www-data 19937  0.0  0.1  13276   372 ?        S    19:54   0:00 /usr/sbin/apache2 -k start
www-data 19939  0.0  0.1  13276   372 ?        S    19:54   0:00 /usr/sbin/apache2 -k start
www-data 19941  0.0  0.1  13276   372 ?        S    19:54   0:00 /usr/sbin/apache2 -k start

---

### Post by d4rk5h4dow5 on 2009-01-02
I also should say that I did open up port 80 on my router

---

### Post by hyper_ch on 2009-01-02
default webfolder is /var/www

Drop your files in there (however it's owned by root, so you might first want to change that). If you want to host multiple sites then say so.

---

### Post by d4rk5h4dow5 on 2009-01-02
How do I change the permission to that file? I think that would help make my life a little easier :)

---

### Post by hyper_ch on 2009-01-02
```

chown

```

---

