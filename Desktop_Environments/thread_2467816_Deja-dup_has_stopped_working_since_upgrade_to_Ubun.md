---
title: "Deja-dup has stopped working since upgrade to Ubuntu-21.04"
date: 2021-10-08
forum: Desktop Environments
---

### Post by stevecoh1 on 2021-10-08
I upgraded to Ubuntu-21.04 (from 20.04->20.10->21.04) and now I find that my deja-dup backup is failing with the following obscure error message:

[FONT=Courier New]Failed to read /tmp/duplicity-6k2ojcdb-tempdir/mktemp-s39ei7up-2: (<class 'EOFError'>, EOFError('Compressed file ended before the end-of-stream marker was reached'), <traceback object at 0x7f80484aaa00>)[/FONT]

A search on this error message produced a similar issue: [https://answers.launchpad.net/duplicity/+question/693039]("https://answers.launchpad.net/duplicity/+question/693039") from 2020 which died for a lack of response.

Can someone provide me some help on how to proceed here to get my backups working again?  Thanks.

---

### Post by ActionParsnip on 2021-10-08
Is /tmp full? You can check with
```

df -h

```

---

### Post by stevecoh1 on 2021-10-08
> **ActionParsnip said:**
> Is /tmp full? You can check with
```

df -h

```

No.

```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           783M  2.3M  781M   1% /run
/dev/sda6       701G  338G  328G  51% /
tmpfs           3.9G  1.1M  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
/dev/sda2        96M   31M   66M  32% /boot/efi
tmpfs           783M   11M  773M   2% /run/user/1001
```

---

