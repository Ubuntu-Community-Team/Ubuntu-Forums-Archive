---
title: "could not 'su' from terminal .. pls help"
date: 2005-12-05
forum: Desktop Environments
---

### Post by index_0@ya.com on 2005-12-05
hi thr, 
       i installed ubuntu yesterday night , with only one user as default. I was able login thru the terminal (as root also)  and also able install packages from synaptic. But the next day, something peculiar , i could nt login from the terminal alone!!! by issing 'su' command ... i always recieve  "Authentication failure  Sorry "  !!! .and synaptic automatically logs in without asking for root password !!! Moreover I can login to gnome session without failure . Now i am stuck with installing frm terminal

Thx in advance

---

### Post by professor_chaos on 2005-12-05
whats the failure you get when logging in as normal user?

Do you know about sudo?

---

### Post by index_0@ya.com on 2005-12-06
hey thx for ur reply .. i found tht only sudo works .. 
it seems su alone cannot be used .

---

### Post by codejunkie on 2005-12-06
[quote=index_0@ya.com]hey thx for ur reply .. i found tht only sudo works .. 
it seems su alone cannot be used .[/quote]
that's normal ubuntu uses sudo by default instead of su like other distros what exactly are you having trouble doing?

---

### Post by cilynx on 2005-12-06
If you need "su" functionality, you can do "sudo su", and give it your sudo password.  That will drop you to a root prompt.

---

### Post by parktownprawn on 2005-12-06
see [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo) for more information about sudo

---

### Post by Aphorism on 2005-12-06
```

sudo -s

```

---

### Post by cilynx on 2005-12-10
One subtle difference I thought worth mentioning:

"sudo -s" give you a root-permission shell with your user's environment variables
"sudo su" give you a root-permission shell with root's environment variables

For my uses, I like having root's environment.  Then again, I don't have anything very important on any given machine so I'm not worried about the "abuse of power" that the root environment gives me.

---

