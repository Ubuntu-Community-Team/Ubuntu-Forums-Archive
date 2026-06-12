---
title: "Wrong backup procedure :("
date: 2009-04-28
forum: General Help
---

### Post by linuxvacuum on 2009-04-28
I made a backup of my whole system with this command
```
nice -n19 ionice -c3 tar -cvpf backup.tar \
--exclude="/lost+found/*" \
--exclude="/proc/*" \
--exclude="/sys/*" \
--exclude="/tmp/*" \
--exclude="/mnt/*" \
--exclude="/media/*" \
--exclude="/var/cache/apt/*" \
--exclude="/var/tmp/*" \
--exclude="$HOME/.opera/cache4/*" \
--exclude="$HOME/.local/share/Trash/*" \
/

```

I then restored it with
```

sudo tar xvpf backup.tar -C /

```

When I booted into it, I had no sound no Internet and my hostname had its name changed to localhost. What did I do wrong?

---

### Post by linuxvacuum on 2009-05-06
This is important.

---

### Post by aparigraha on 2009-05-06
> **linuxvacuum said:**
> I made a backup of my whole system with this command
```
nice -n19 ionice -c3 tar -cvpf backup.tar \
--exclude="/lost+found/*" \
--exclude="/proc/*" \
--exclude="/sys/*" \
--exclude="/tmp/*" \
--exclude="/mnt/*" \
--exclude="/media/*" \
--exclude="/var/cache/apt/*" \
--exclude="/var/tmp/*" \
--exclude="$HOME/.opera/cache4/*" \
--exclude="$HOME/.local/share/Trash/*" \
/

```

I then restored it with
```

sudo tar xvpf backup.tar -C /

```

When I booted into it, I had no sound no Internet and my hostname had its name changed to localhost. What did I do wrong?
You might want to exclude the backup.tar file as well. Otherwise you can get weird results.

So maybe add --exclude=/backup.tar

I always use the method explained [URL="http://ubuntuforums.org/showthread.php?t=35087"]here
[/URL] and it hasn't failed me yet.

---

