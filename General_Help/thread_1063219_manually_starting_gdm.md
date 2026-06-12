---
title: "manually starting gdm"
date: 2009-02-07
forum: General Help
---

### Post by anand77 on 2009-02-07
Is it possible to install ubuntu such that it always boot in text mode but able to run gnome applications? or start gdm when you want to run a gui based application and when its done switch back to text mode?

---

### Post by dcstar on 2009-02-07
> **anand77 said:**
> Is it possible to install ubuntu such that it always boot in text mode but able to run gnome applications? or start gdm when you want to run a gui based application and when its done switch back to text mode?

Yes, this question has been answered many times previously and details can be searched out.

---

### Post by The Cog on 2009-02-07
You could rename /etc/rc2.d/gdm like this:
```
sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/K30gdm
```

Then you can start/stop gdm like this:
```
sudo /etc/init.d/gdm start
sudo /etc/init.d/gdm stop
```
Or you can bypass the login screen that gdm gives you by just usig the command **startx**.

---

