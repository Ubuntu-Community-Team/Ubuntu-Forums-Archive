---
title: "Starting and setting up italc"
date: 2016-02-06
forum: Education &amp; Science
---

### Post by daryl9 on 2016-02-06
Hello All,

I am setting up several computers for a couple of schools in the Philippines.  I thought that I would try using italc for the teacher/student systems, however, I can't even get the darn think to working and documentation is very limited.

I installed italc on a a master system that I will give to the teacher, and then on some of the clients.  When I try to start the master, I get:

 "No authentication key files were found or your current ones are outdated. Please create new key files using the ITALC Management Console.  Alternatively set up log authentication using the ITALC Management Console.  Otherwise you won't be able to access computer using ITALC."

Took me a while to figure out that the Management Console was its own app and that it had to started via a command window.  Once I started the management console, I was able to create key's.  Okay, great, however, I still get the same error.  Also, I'm assuming that an italc service of some kinds needs to be running, but I have no idea what it is, or how to start it.  There is nothing in the documentation that talks about starting a Linux daemon, only a Windows service.

I would appreciate any help anyone can provide.

Thank you.

Daryl

---

### Post by newbie-user on 2016-02-07
Did you copy the public key from the master to the clients?

```
scp /etc/italc/keys/public/teacher/key root@[client]:/etc/italc/keys/public/key
```

Also italc does not seem to be in active development anymore. Have you looked at epoptes?

---

