---
title: "automatic shutdown"
date: 2006-07-21
forum: Desktop Environments
---

### Post by ubun_nv on 2006-07-21
is there is any automatically shutdown utility for linux?

---

### Post by bulldog on 2006-07-21
Not by my knowing,but why?
When you leave your computer you can easely shut it down,or leave it running and lock your desktop.

---

### Post by Thund3rstruck on 2006-07-21
Yup...

```

$ sudo crontab -e

```

Set your shutdown schedule in the crontab and run this command as the entry

```

$ shutdown -h now

```

---

### Post by jordilin on 2006-07-21
> **Thund3rstruck said:**
> Yup...

```

$ sudo crontab -e

```

Set your shutdown schedule in the crontab and run this command as the entry

```

$ shutdown -h now

```

You can also try shutdown -h +6 and your computer will shut down in six minutes or the time you specify.

---

