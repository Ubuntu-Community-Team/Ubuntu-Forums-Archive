---
title: "update issue"
date: 2009-05-24
forum: General Help
---

### Post by jcm1107 on 2009-05-24
when I check for updates I get this message and cannot find any updates. I am using 8.04 hardy.


W: Failed to fetch [http://deb.mulx.net/dists/hardy/Release.gpg](http://deb.mulx.net/dists/hardy/Release.gpg)  Could not resolve 'deb.mulx.net'

W: Failed to fetch [http://deb.mulx.net/dists/hardy/main/i18n/Translation-en_US.bz2](http://deb.mulx.net/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'deb.mulx.net'

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by colau on 2009-05-24
May be,this is not a serious problem.

---

### Post by jcm1107 on 2009-05-24
> **colau said:**
> May be,this is not a serious problem.

It may not be serious I was just concerned that I get an error and can not find the sources.

---

### Post by jcm1107 on 2009-05-24
bump! Anyone know why These links don't work? Do I need to change anything in the sources that updater uses?

---

### Post by abyrne on 2009-05-24
Is the server down or de-commissioned? Some times one bad server can screw up the entire update list.

---

### Post by jcm1107 on 2009-05-24
> **abyrne said:**
> Is the server down or de-commissioned? Some times one bad server can screw up the entire update list.

I don't know much about the sources but I tried the web address and it didn't work so mabe it is down. I just want to know anything I can add to my sources or remove to get it to work again. Can anyone help me?

---

### Post by abyrne on 2009-05-24
Go to "Software Sources" and delete the line (or two lines, in case you added a source code line) that contains the faulty server.

---

### Post by jcm1107 on 2009-05-24
> **abyrne said:**
> Is the server down or de-commissioned? Some times one bad server can screw up the entire update list.

Thanks!!! I think I solved the issue. I removed the check mark by the  source that was not working and tried to update. It didn't find any updates, but now says your package information was last updated less than an hour ago. Instead of 15 days ago like it used to say. I don't get the error message anymore so I think I solved my problem.

---

