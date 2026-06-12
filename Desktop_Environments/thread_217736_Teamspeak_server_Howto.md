---
title: "Teamspeak server Howto"
date: 2006-07-17
forum: Desktop Environments
---

### Post by elglas on 2006-07-17
after messing around with this for a while, I finally got it to work

for dapper:

$ sudo apt-get install sqlite

download the beta teamspeak binary, and the other one

$ cp /usr/lib/libsqlite.so.0 /home/user/whereever_you_put_Teamspeak/

and rename it to sqlite.so

and all will be well...

---

