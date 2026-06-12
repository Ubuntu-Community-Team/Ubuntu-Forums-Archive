---
title: "Can't login after upgrading to Jaunty Jackalope"
date: 2009-04-27
forum: General Help
---

### Post by sakpgu on 2009-04-27
Greetings:
--Newbie here with an odd problem: can't login to my desktop PC with the GUI after upgrading to Jaunty Jackalope from Kubuntu 8.10.
--There is no error message with either of the two accounts setup on the machine. After typing the password in the login box and hitting enter, the screen blanks like it's logging in and then returns to a login prompt. I can, however, login as either user from the terminal; however, I don't yet know enough commands to make a difference. 
--I did notice that the machine name in the login box now reads, "Welcome to localhost.localdomain" instead of the old machine name. Other than that, everything looks the same. 
--Thanks in advance for any and all suggestions.
Patrick

---

### Post by spiderbatdad on 2009-04-27
I searched ubuntu login loop with google and see a number of possibilities...but it looks like something might be missing in your /etc/hosts file...not suggested by google results...so check out those maybe, or maybe boot into recovery from grub and have a look at /etc/hosts. It should have a machine name associated with 127.0.0.1 and aliases after like localhost.localdomain. For example:
```
127.0.0.1	some_user-laptop	localhost.localdomain	localhost
127.0.1.1	some_user-laptop

```

---

