---
title: "Search/Analys for files in /, but skip /home"
date: 2013-03-07
forum: Desktop Environments
---

### Post by Azyx on 2013-03-07
Hi I wonder how I can search/ for files in the /-directory, but skip /home? My / is a partition and going to be full (20GB) and what see what's files that filled up the partition. Run 10.04LTS
Cheers

---

### Post by steeldriver on 2013-03-07
If /home really is on a separate partition, then iirc the -xdev option should prevent 'find' from descending into it

```
find / -xdev ...
```

OTOH if you need to exclude a path on the same partition, you can try prune

```
find / -path '/home' -prune -o ...
```

(needs the -o before your remaining tests because the default is to AND them)

---

### Post by Azyx on 2013-03-07
> **steeldriver said:**
> If /home really is on a separate partition, then iirc the -xdev option should prevent 'find' from descending into it

```
find / -xdev ...
```

OTOH if you need to exclude a path on the same partition, you can try prune

```
find / -path '/home' -prune -o ...
```

(needs the -o before your remaining tests because the default is to AND them)


I have think something more desktop oriented search or space analysing tools (Disk spaca analyzer or nautilus that only search for bigger files.or some other application there file-size or other may... How can I get rid of files, that I don't need any more, including uninstall applications....

---

