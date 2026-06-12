---
title: "What is copyto.sh?"
date: 2009-01-23
forum: Desktop Environments
---

### Post by mister_p_1998 on 2009-01-23
Strange thing today, my cpu was maxing out, and when I ran Atop, there were two zombies, and four instances of a script called copyto.sh, its not one Ive written, and I did a search in Home and the full filesystem. Nothing was found, is it a system created script? Im running Dapper.
Steve

---

### Post by XanTrax on 2009-01-23
> **mister_p_1998 said:**
> Strange thing today, my cpu was maxing out, and when I ran Atop, there were two zombies, and four instances of a script called copyto.sh, its not one Ive written, and I did a search in Home and the full filesystem. Nothing was found, is it a system created script? Im running Dapper.
Steve

I do not know your level of linux knowledge but can you please run these commands and post the output.

```

sudo su -
cd /
find * | grep -i "copyto.sh"

```

---

### Post by mister_p_1998 on 2009-01-23
> **XanTrax said:**
> I do not know your level of linux knowledge but can you please run these commands and post the output.

```

sudo su -
cd /
find * | grep -i "copyto.sh"

```


Aha!
It was Amarok!

root@ubuntu:/# find * | grep -i "copyto.sh"
home/steve/.kde/share/apps/amarok/scripts/copyto/copyto.sh

I was trying to play MP3's off my server.
Thanks
Steve

---

### Post by XanTrax on 2009-01-24
> **mister_p_1998 said:**
> Aha!
It was Amarok!

root@ubuntu:/# find * | grep -i "copyto.sh"
home/steve/.kde/share/apps/amarok/scripts/copyto/copyto.sh

I was trying to play MP3's off my server.
Thanks
Steve

No problem, glad I could help :p.

---

