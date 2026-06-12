---
title: "Disallow non absolute dirs in updatedb.conf (PRUNEPATHS)"
date: 2006-06-21
forum: Desktop Environments
---

### Post by Sam on 2006-06-21
Hi

I would like to prune the .svn directories of my svn projects, which flood my results when I slocate something.

So I had a look in /etc/updatedb.conf and I changed PRUNEPATHS. I added .svn in the list, doesn't work after an updatedb, I tried ./.svn, same result.

Anyone knows a way to disallow non absolute directories with updatedb ???

Thanks

---

### Post by hugmenot on 2008-03-26
Did you find a way to get rid of the .svn/* clutter?

---

### Post by Sam on 2008-03-26
Still not yet... :(

But thanks for bumping maybe someone will enlighten us !

---

### Post by gungazoo on 2008-06-18
I put this in my PRUNEPATHS line and it seems to work:

     */.svn/*

Hope it helps.

Peter

---

### Post by hugmenot on 2008-06-20
No it doesn&#8217;t. At least here.

```
PRUNEPATHS="/tmp /var/spool /media */.svn/* /var/cache"

```

Is your locate is provided by the mlocate package? Or do you still have slocate?

---

