---
title: "Repos not working"
date: 2006-06-11
forum: Desktop Environments
---

### Post by k3rnel on 2006-06-11
Hi, I'm experiencing a problem with the repos.
When trying to update, I get 403 forbidden errors while apt attemps to download the indexes, example: "http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz: 403 Forbidden
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:) 403 Forbidden".
I had the repos like [http://au.archive](http://au.archive)...., I tried to use my countrycode instead of 'au',  tried not using country codes at all as in the example, tried ftp instead of http, but nothing seems to work. I don't have any network problems and can access the index files and browse through the repos manually.

Any ideas?

Edit: Changing Acquire::http::Proxy "false"; to Acquire::::Proxy "false"; solved the problem, it now downloads all indexes except 1, which gives a bz2 opening error, odd.

---

