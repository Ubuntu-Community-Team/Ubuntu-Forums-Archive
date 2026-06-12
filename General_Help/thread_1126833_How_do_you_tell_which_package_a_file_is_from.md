---
title: "How do you tell which package a file is from?"
date: 2009-04-15
forum: General Help
---

### Post by scott8035 on 2009-04-15
I'm new to Ubuntu and the apt/dpkg system. Can someone please tell me how you find out what package a given file is from?
---scott

---

### Post by Titan8990 on 2009-04-15
As far as I know, not possible. If it was, I wouldn't be surprised if it involved skills with sed and awk.

What purpose would this serve?

---

### Post by maheshasolkar on 2009-04-15
I doubt if there is a sure-shot way of telling which package a file belongs to. I would google the name of file with, say, 'ubuntu package' or something to that effect. May be it will give some clue. I would also try 'site:launchpad.net' in the search query.

---

### Post by scott8035 on 2009-04-15
> **Titan8990 said:**
> What purpose would this serve?

In this case, I'm having a problem with /usr/lib/notify-osd/notify-osd running out of control, and I wanted to know what package it came from so I could use ubuntu-bug on it and file a report.

---

### Post by codeseer on 2009-04-15
```

dpkg -S filename

```

If you don't have the file/package on your system, you can use:

```

sudo apt-file update
apt-file search filename

```

---

### Post by maheshasolkar on 2009-04-15
> **scott8035 said:**
> In this case, I'm having a problem with /usr/lib/notify-osd/notify-osd running out of control, and I wanted to know what package it came from so I could use ubuntu-bug on it and file a report.

Well in this specific case, the package seems to be notify-osd:

  [https://launchpad.net/ubuntu/+source/notify-osd](https://launchpad.net/ubuntu/+source/notify-osd)

---

### Post by Titan8990 on 2009-04-15
> **codeseer said:**
> ```

dpkg -S filename

```

If you don't have the file/package on your system, you can use:

```

sudo apt-file update
apt-file search filename

```

Good info. I found dpkg -S worked in Debian but it does not have apt-file.

---

### Post by codeseer on 2009-04-15
> **Titan8990 said:**
> Good info. I found dpkg -S worked in Debian but it does not have apt-file.

Ubuntu doesn't either; it has to be installed from the repository.

---

### Post by scott8035 on 2009-04-15
Thanks much!
---scott

---

