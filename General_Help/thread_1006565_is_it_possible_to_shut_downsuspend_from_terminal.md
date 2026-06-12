---
title: "is it possible to shut down/suspend from terminal?"
date: 2008-12-09
forum: General Help
---

### Post by das867 on 2008-12-09
i just want to know, is it possible to shutdown or suspend from terminal without root? I've been working on some remote commands sent by email, where sending passwords isn't really an option, so i was just wondering if this was possible, and if so, how?

---

### Post by rudihawk on 2008-12-09
Well to shutdown:

```
sudo poweroff -n
```

Should work

---

### Post by das867 on 2008-12-09
i did say without root, which includes sudo, gksudo, su and any other variations, so no that doesn't really work.

---

### Post by gjoellee on 2008-12-09
no, without having root access your system cannot access the files needed to do a shutdown or suspend.

---

### Post by das867 on 2008-12-09
ah, thank you very much. since theres no way to do it without root, would there be anyway to give a specific script root access by default, but not have to be root to run it?

---

### Post by p_quarles on 2008-12-09
Not without root, no. There are ways of working around that, but it's an extremely bad idea to allow anyone in the world to shut off your computer remotely.

---

### Post by p_quarles on 2008-12-09
> **das867 said:**
> ah, thank you very much. since theres no way to do it without root, would there be anyway to give a specific script root access by default, but not have to be root to run it?
There are ways of running as root without password authentication. This isn't something this forum can support, though, because as I said this is an enormously bad idea.

Run an SSH daemon and use that to poweroff. Alternatively, there is cron. Those are the sane ways to do what you want. E-mailing commands to your server is not.

---

