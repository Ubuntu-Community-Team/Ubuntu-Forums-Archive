---
title: "Getdeb/Playdeb both down"
date: 2012-12-11
forum: Gaming &amp; Leisure
---

### Post by headcheese3 on 2012-12-11
The last thread that I've seen talking about this was in 2010. I've noticed that they're both down. Does anyone know why? Maintenance? Updating? 

Note: It's been a couple days now. I also don't know when it started (given that I don't check regularly).

Many Thanks,
headcheese3

[SOLVED]

---

### Post by headcheese3 on 2012-12-11
Nevermind. Solved. This is why: [http://blog.getdeb.net/2012/12/server-downtime.html](http://blog.getdeb.net/2012/12/server-downtime.html)

---

### Post by holastickboy on 2012-12-11
> **headcheese3 said:**
> Nevermind. Solved. This is why: [http://blog.getdeb.net/2012/12/server-downtime.html](http://blog.getdeb.net/2012/12/server-downtime.html)

Thank the computer gods! Would be devastated if Playdeb died!

---

### Post by MasterNetra on 2012-12-11
Yea been down for a little while I guess, sense from 5th at least, based on a mint linux forum post. Meanwhile there is the backups.

[http://www.ubuntugeek.com/getdeb-mirror-site.html](http://www.ubuntugeek.com/getdeb-mirror-site.html)

---

### Post by schurtek on 2013-01-02
Okay, it's now January and it's still down? Any idea what is going on?

---

### Post by Virus666 on 2013-01-15
> **schurtek said:**
> Okay, it's now January and it's still down? Any idea what is going on?

Just uncheck the GetDeb/PlayDeb repos from software sources and add an alternate mirror. Such as:

deb [http://mirrors.dotsrc.org/getdeb/ubuntu](http://mirrors.dotsrc.org/getdeb/ubuntu) [COLOR=Red]version[/COLOR]-getdeb apps games

Versions:

- ubuntu 10.04 lucid lynx - linux mint 9 isadora: [COLOR=Red]lucid[/COLOR]
- ubuntu 10.10 maverick meerkat - linux mint 10 julia: [COLOR=Red]maverick[/COLOR]
- ubuntu 11.04 natty narwhal - linux mint 11 katya: [COLOR=Red]natty[/COLOR]
- ubuntu 11.10 oneiric ocelot - linux mint 12 lisa: [COLOR=Red]oneiric[/COLOR]
- ubuntu 12.04 precise pangolin - linux mint 13 maya: [COLOR=Red]precise[/COLOR]
- ubuntu 12.10 quantal quetzal - linux mint 14 nadia: [COLOR=Red]quantal[/COLOR]

**If** that is the **first time** for you to add GetDeb repos, you will need to add software source key:

Open terminal and paste:

```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A8A515F046D7E7CF

sudo apt-get update
```

---

### Post by pqwoerituytrueiwoq on 2013-01-19
we have some new news
[https://plus.google.com/u/0/+getdeb/posts/FF1gRuZN7pM](https://plus.google.com/u/0/+getdeb/posts/FF1gRuZN7pM)

---

