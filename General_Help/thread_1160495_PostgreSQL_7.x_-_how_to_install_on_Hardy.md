---
title: "PostgreSQL 7.x - how to install on Hardy?"
date: 2009-05-15
forum: General Help
---

### Post by nexus10 on 2009-05-15
Hi,
I'd like to install PostgreSQL 7 -- ideally 7.4.19, but 7.4.x would be fine and probably 7.x would work. This is required by an existing package that does not support pg 8.*). Is there a supported repository that still has pg7?

I've enabled universe and multiverse, and
```
apt-get install -sV 'postgresql=8*'
```
shows me that pg 8.3.7 is available, but
```
apt-get install -sV 'postgresql=7*'
```
shows nothing. How do I find a repository that contains a stable, patched pg7 release?

If there is no officially maintained release, please could someone point me to instructions either on (a) tracking down an unofficial repo, or (b) installing from source in a way that does not conflict with apt-get? So far my searches for any of the above have proved unfruitful.

Thanks for your attention,
Thomas.

---

### Post by nexus10 on 2009-05-16
Ok, replying to my own post in woefully sad style, in case I or anyone else need(s) this in the future.

1. Add dapper repos to /etc/apt/sources.list:
```
deb http://gb.archive.ubuntu.com/ubuntu dapper main universe
```
2. Pin postgresql to dapper so that it does not get upgraded, creating /etc/apt/preferences:
```

Package: postgresql
Pin: release a=dapper
Pin-Priority: 900

Package: postgresql-client
Pin: release a=dapper
Pin-Priority: 900

```

Standard installation now installs 7.4, and warns me that it is unsupported:
```
sudo apt-get install postgresql
```

That's it.

-- Thomas.

---

