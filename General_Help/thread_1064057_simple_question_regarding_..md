---
title: "simple question regarding ./"
date: 2009-02-08
forum: General Help
---

### Post by andreasis on 2009-02-08
The absolute beginner forum seems to have been archived, so...

I want to execute /etc/rc.local using a single command

sudo ./etc/rc.local does not work

cd /etc
sudo ./rc.local
works, but how would I combine this into one command?

Is there an alternative to

cd /etc && sudo ./rc.local

---

### Post by taurus on 2009-02-08
You don't need to put ./ in front if you use the absolute path.

```
sudo /etc/rc.local
```

---

### Post by RudolfMDLT on 2009-02-08
"./" means "from my current or working directory"

This is worth reading of you have the time - it's short! :)
[http://en.wikipedia.org/wiki/Working_directory](http://en.wikipedia.org/wiki/Working_directory)

---

### Post by andreasis on 2009-02-08
Thanks very much to both of you.

Just what I was looking for; and more.

This forum doesn't fail to impress.

---

### Post by andreasis on 2009-02-08
PS: Is there no way to mark threads as [SOLVED] anymore?

---

