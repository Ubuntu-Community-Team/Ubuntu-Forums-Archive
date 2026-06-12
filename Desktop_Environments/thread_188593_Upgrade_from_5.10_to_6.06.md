---
title: "Upgrade from 5.10 to 6.06"
date: 2006-06-04
forum: Desktop Environments
---

### Post by stiankarlsen on 2006-06-04
Currently running BreezyBadger 5.10, and I'm trying to get dapper 6.06, updating using the update manager, where I can click "upgrade" and 6.06 LTS should be installed. 

I keep getting this error, and the thing just shuts down.
> Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/bre...urce/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/bre...urce/Sources.gz) Sub-process gzip returned an error code (1)


What can I do?

---

### Post by shrift on 2006-06-04
Here are my Dapper repositories, they work. Add them/make sure they are in you /etc/apt/sources.list


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

---

### Post by stiankarlsen on 2006-06-05
Thanks but i got it working, just replaced everyhing that said breezy with dapper  in my sources.list file, and it worked :)

---

### Post by shrift on 2006-06-05
Good.

---

