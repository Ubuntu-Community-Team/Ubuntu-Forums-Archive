---
title: "Get cedega to install games on external HD"
date: 2007-05-24
forum: Gaming &amp; Leisure
---

### Post by martinrandau on 2007-05-24
The title says it all: how can I get cedega to install my games on the external HD /dev/sdb1? I am running out of space on my root partition which is where cedega installs my games.

Would it work to replace .cedega with a link to the external HD?

Thanks!

---

### Post by Cappy on 2007-05-24
Yes, linux makes it incredibly easy (unlike windows where you have to search and replace registry keys)

```

cd ~
cp -r ~/.cedega /media/sdb1
mv .cedega .cedegabackup
ln -s /media/sdb1/.cedega .cedega 

```

this copies all the directories with all subfolders
and makes a soft link to it with ln -s <target> <the link>

This assumes /dev/sdb1 is mounted at /media/sdb1

---

