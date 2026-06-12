---
title: "Could not update ICEauthority file"
date: 2010-12-18
forum: Desktop Environments
---

### Post by jimmy8910 on 2010-12-18
I've just installed Ubuntu 10.04 onto my system and have been getting an error message right after i enter my password to login
"Could not update ICEauthority file /home/jimmy/.ICEauthority"
I can close this and everything seems to work fine.
I have no idea as to why i get this error and how do i get rid of it.

I tried using one of the suggestions and entered the command    

```
sudo chown jimmy:jimmy .ICEauthority
```

got an input/output error for this


I've checked the permissions using the following command[FONT=monospace]

[/FONT]```
ls -l home/jimmy/.ICEauthority
```

got the following output

-rw------- 1 jimmy jimmy 0 2010-12-18 22:55 /home/jimmy/.ICEauthority

---

### Post by jimmy8910 on 2010-12-19
How do i close this thread?

---

