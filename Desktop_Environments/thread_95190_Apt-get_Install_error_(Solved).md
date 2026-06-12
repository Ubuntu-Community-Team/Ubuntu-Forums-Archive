---
title: "Apt-get Install error (Solved)"
date: 2005-11-25
forum: Desktop Environments
---

### Post by fnando on 2005-11-25
The update icon on my tray says that I have updates pending.

But when I try to update my system I receive the following error:

```

dpkg: parse error, in file `/var/lib/dpkg/status' near line 5601 package `xkeyboard-config':
 missing version

```

I tried the following commands, without success.

```

sudo apt-get -f install
sudo apt-get upgrade

```

Any tip?

Thanks!

---

### Post by Xian on 2005-11-26
Well, basically your status file is corrupted. You can attempt to fix it by going to the line number mentioned and editing what is there to include the missing version information, or you can copy over the status-old file which is the backup as your new status file. Hopefully, it is still in good shape.

---

### Post by fnando on 2005-11-26
[quote=Xian]Well, basically your status file is corrupted. You can attempt to fix it by going to the line number mentioned and editing what is there to include the missing version information, or you can copy over the status-old file which is the backup as your new status file. Hopefully, it is still in good shape.[/quote]

Can you tell what's the path to the old file?

---

### Post by Xian on 2005-11-26
/var/lib/dpkg/status-old

---

### Post by fnando on 2005-11-26
Alright.

On /etc/apt/ I have some files:

```

sources.list
sources.list_backup
sources.list.save
sources.list~

```

Just replace sources.list with sources.list_backup?

---

### Post by fnando on 2005-11-26
[quote=Xian]/var/lib/dpkg/status-old[/quote]

Saw your reply now! ;)

---

### Post by fnando on 2005-11-26
```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status_backup
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get install

```

This lines did the trick! And I installed all the pending updates!

Thanks a lot Xian!

---

