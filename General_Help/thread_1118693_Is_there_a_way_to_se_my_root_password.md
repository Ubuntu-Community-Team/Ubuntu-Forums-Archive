---
title: "Is there a way to se my root password ?"
date: 2009-04-07
forum: General Help
---

### Post by hoboy on 2009-04-07
I am trying to install an oracle db, I have to login as root.
I am trying this

luc@ubuntu:~$ su root
Password: 
su: Authentication failure
luc@ubuntu:~$

---

### Post by Simian Man on 2009-04-07
Ubuntu locks the root account.  You can unlock it, but there is some policy against saying how.

Alternatively you can get a root shell by doing:
```

sudo su

```

Then entering your regular password.  You can also execute single commands with sudo as follows:
```

sudo command

```

Where command is a single command you wish to run at root privilege.

---

### Post by bodhi.zazen on 2009-04-07
You obtain a root shell with :

```
sudo -i
```

---

### Post by absolutezero1287 on 2009-04-07
Become root with sudo -s

---

### Post by bodhi.zazen on 2009-04-07
> **absolutezero1287 said:**
> Become root with sudo -s

sudo -i is preferred to sudo -s , -i scrubs the environmental variables.

---

### Post by absolutezero1287 on 2009-04-07
> **bodhi.zazen said:**
> sudo -i is preferred to sudo -s , -i scrubs the environmental variables.

I see, I never knew that. I learn something new everyday. :)

---

### Post by Kosimo on 2009-04-07
Sometimes is cool to feel the sudo power for a while :D


[IMG]http://imgs.xkcd.com/comics/sandwich.png[/IMG]

---

### Post by LowSky on 2009-04-07
Kosimo I love that drawing, very funny linux joke.

---

### Post by bodhi.zazen on 2009-04-07
> **absolutezero1287 said:**
> I see, I never knew that. I learn something new everyday. :)

:twisted:

---

