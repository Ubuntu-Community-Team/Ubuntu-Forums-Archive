---
title: "&quot;apt-get install libmysqlclient15-dev&quot; issue"
date: 2009-02-18
forum: General Help
---

### Post by dlebowski on 2009-02-18
Is it suppose to take 15 hours for me to run this?  I am running this for an application I am wanting to run on Ubuntu Server, but it hangs and says it's going to take 15 hours to complete.  Any ideas?  Thanks.

Ryan

---

### Post by mikewu on 2009-02-18
Just installed it in 8 seconds. You might want to check your internet connection. Seems to be working over here though.

apt-get shouldn't hang like this. Try killing the process and running the command again. Can't really think of any possible reason for this happening.

---

### Post by dlebowski on 2009-02-18
Maybe it's a DNS problem.  Where do I specify DNS in ubuntu server?  Thanks for your quick reply.

Ryan

---

### Post by dlebowski on 2009-02-18
Actually, it's not a DNS problem.  I can ping the download site from the ubuntu server.  I am going to restart the server and try again.  I have only had problems with these commands:

apt-get install build-essential
apt-get install libmysqlclient15-dev
apt-get install python-dev

---

### Post by yaarrabba on 2009-08-26
Thanks dlebowski. I had problem installing MySQLdb api for python. You're post solved it in no time. 

Thanks

---

