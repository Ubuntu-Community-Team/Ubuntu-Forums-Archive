---
title: "how to fix it?"
date: 2009-01-05
forum: General Help
---

### Post by superpink99 on 2009-01-05
ok ive been tweaking with my ubuntu and i think i messed up with my DNS settings and the like, now what do i do to fix this problems, coz my firefox isn't working well....

what do i do so that ubuntu will check itself and fix any problems with the DNS settings and others.........

---

### Post by redilyn on 2009-01-05
What exactly is the problem you are having? Your post isn't very clear.

if you are having DNS issues you could try using the opendns servers

```

sudo gedit /etc/resolv.conf

```

The make the following change.
```

nameserver 208.67.220.220 
nameserver 208.67.222.222

```

Your dns entries should only be a problem if you are using a static ip or your isp frequently has dns server problems.

If you have a dynamic ip your dns servers will be reset when your ip is renewed.

---

