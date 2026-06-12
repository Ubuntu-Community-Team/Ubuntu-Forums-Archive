---
title: "sudo: unable to resolve host dell"
date: 2008-12-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LesFromWaldenVT on 2008-12-08
I don't recall when this started to occur but every time I enter 'sudo' a) it takes a long time (up to 10 seconds), b) it always says "sudo: unable to resolve host dell". I'm sure this is not good but I don't know what it portends.
Does anyone know what i need to change to get rid of this 'problem'?

Thanks,
Les

---

### Post by doas777 on 2008-12-08
check your hosts file:
```

gksu gedit /etc/hosts

```

your looking for a pair of lines like:
```

127.0.0.1	localhost
127.0.1.1	dell

```

most of the time, that error means that 'Dell' has been changed to a DNS name like Dell.<Domain>.net or whatever. just remove the end, leaving only the host name 'dell'.
you need the line with 'dell' in order to sudo (though who knows why).

Network Manager in Gutsy did that to me all the time....
good luck

---

