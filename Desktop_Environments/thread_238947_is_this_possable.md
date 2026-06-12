---
title: "is this possable?"
date: 2006-08-18
forum: Desktop Environments
---

### Post by sal on 2006-08-18
i would like to know if it's possable to have a scrip of some sort set up to take a full screenshot of my kubuntu desktop once a day at a random time and save it to a specific directory.

Im running kubuntu dapper 6.06.1
 
thanks in advance for any help

---

### Post by kb3hkg on 2006-08-18
it is defintely possible to do that. The script would just have to invoke a program like ksnapshot.

As for when it would run you can make it a specific time and just use cron, if you want random you will probably have to make it run in the background all the time and have it randomly pick a time.

---

### Post by sal on 2006-08-18
do you know how to write such a script?
if so could you help me with it.
thanks.

---

### Post by kb3hkg on 2006-08-21
It would be easiest to do in perl, however due to recent commitments of my time I don't have time to help out. Unfortunately I haven't found a way for open source to pay my bills yet.

---

