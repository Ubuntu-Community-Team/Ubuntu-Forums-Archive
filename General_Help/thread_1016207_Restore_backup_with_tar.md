---
title: "Restore backup with tar"
date: 2008-12-19
forum: General Help
---

### Post by philetus on 2008-12-19
I'm ready to restore my tar backup, but I don't want to include the old boot settings.

If I add " --exclude=/boot", will that do the trick? Probably not.

How about if I rename boot to boot.old and create a new, empty boot folder?

---

### Post by jerome1232 on 2008-12-19
> **philetus said:**
> I'm ready to restore my tar backup, but I don't want to include the old boot settings.

If I add " --exclude=/boot", will that do the trick? Probably not.

How about if I rename boot to boot.old and create a new, empty boot folder?

Yes using the --exclude option should work I just tested it out and it seems to be functioning as expected.

I created an archive that only contained the folder Python, when I extracted (verbosity on to show what get's extracted) with the --exclude option it didn't exctract the Python folder.
```

jeremy@direbane:~/Documents$ tar cf test.tar Python
jeremy@direbane:~/Documents$ tar xvf test.tar --exclude Python
jeremy@direbane:~/Documents$ rm test.tar

```

---

