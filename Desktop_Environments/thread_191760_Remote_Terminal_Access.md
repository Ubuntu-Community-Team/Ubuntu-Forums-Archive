---
title: "Remote Terminal Access"
date: 2006-06-07
forum: Desktop Environments
---

### Post by underdog on 2006-06-07
I'm running 6.06 on a p3 w/ 256MB of ram. 

I want to, basically, be able to use it remotely like a unix shell account.

I don't know if I am using the wrong search terms or what, but I can't find much on it. I think I might need freenx? Is that what I should use? I want to be able to get/put files from the machine from other machines, mostly.
Thanks

---

### Post by nanotube on 2006-06-08
[QUOTE=underdog]I'm running 6.06 on a p3 w/ 256MB of ram. 

I want to, basically, be able to use it remotely like a unix shell account.

I don't know if I am using the wrong search terms or what, but I can't find much on it. I think I might need freenx? Is that what I should use? I want to be able to get/put files from the machine from other machines, mostly.
Thanks[/QUOTE]
if you just want to use it remotely in text mode, all you need is an ssh server running on your machine. and all you need to do that is to install the openssh-server package.
```
sudo aptitude update
sudo aptitude install openssh-server
```

once you do that, you will be able to connect to your machine using any ssh client, and for file transfer, any sftp client.

freenx is if you want to do something like remote desktop. but for text mode, ssh is what you need.

---

### Post by underdog on 2006-06-08
Wow ok thank you. Is that aptitutude a shortcut for apt-get i guess?

---

### Post by taurus on 2006-06-08
[QUOTE=underdog]Wow ok thank you. Is that aptitutude a shortcut for apt-get i guess?[/QUOTE]
Aptitude is the new thing that Debian is using now...

---

### Post by nanotube on 2006-06-08
[QUOTE=underdog]Wow ok thank you. Is that aptitutude a shortcut for apt-get i guess?[/QUOTE]
what taurus says is right, but here is more detail:

aptitude is Better than apt-get. it is smarter about tracking dependencies and basically gives you less problems. generally a good idea to use it instead of apt-get. the syntax is all the same, except you substitute "aptitude" instead of "apt-get".

---

