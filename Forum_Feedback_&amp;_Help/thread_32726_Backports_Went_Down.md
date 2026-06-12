---
title: "Backports Went Down"
date: 2005-05-09
forum: Forum Feedback &amp; Help
---

### Post by XDevHald on 2005-05-09
Just to let everyone know that the Backports are down at the moment, so please note that this has been notified to the one who is running the 3rd Party Projects

---

### Post by RadioImp on 2005-05-09
Ah, thanks for the notice, wondered why things weren't updating properly.

---

### Post by ubuntu-geek on 2005-05-09
fixing

---

### Post by sandyeggoboy on 2005-05-09
[QUOTE=ubuntu-geek]fixing[/QUOTE]


i too had been seeing this ... now I know. Thanks for the update!!!

---

### Post by rayde on 2005-05-09
looks to be working for me now

---

### Post by jdong on 2005-05-10
[http://ubuntuforums.org/showthread.php?p=165370](http://ubuntuforums.org/showthread.php?p=165370)

I'm still getting user reports about slow repo access... hmm....

---

### Post by pdt677 on 2005-05-10
I was getting 1 - 5 kB/s when I did
```
wget http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/binary-i386/mozilla-firefox_1.0.3-2%7E5.04ubp1+1.0.2-0ubuntu5_i386.deb
```

this morning (and last night at home too) on an otherwise very fast connection.   :???:

---

### Post by deception on 2005-05-11
Working good here, thanks for fixing guys  :grin: 

And also thanks to the team that deals with b/p, I am very much grateful!

---

### Post by k-sea on 2005-05-16
looks like backports is running into this error again. Haven't seen a new post on this topic so though I would just ad to this one. was up on saturday but down sunday and still today.

W: Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/](http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/)

  500 Internal Server Error

W: Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-backports-staging/main/](http://backports.ubuntuforums.org/backports/dists/hoary-backports-staging/main/)

  500 Internal Server Error

Regards,

Casey

---

### Post by XDevHald on 2005-05-16
[QUOTE=k-sea]looks like backports is running into this error again. Haven't seen a new post on this topic so though I would just ad to this one. was up on saturday but down sunday and still today.

W: Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/](http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/)

  500 Internal Server Error

W: Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-backports-staging/main/](http://backports.ubuntuforums.org/backports/dists/hoary-backports-staging/main/)

  500 Internal Server Error

Regards,

Casey[/QUOTE]
 Yeah, it happens just need'em to get a cleanup is all ;)

---

### Post by jdong on 2005-05-16
```

pid 9088 (httpd), uid 80: exited on signal 6
pid 11917 (httpd), uid 80: exited on signal 6
pid 11909 (httpd), uid 80: exited on signal 6
pid 11901 (httpd), uid 80: exited on signal 6
pid 11928 (httpd), uid 80: exited on signal 6
pid 16010 (httpd), uid 80: exited on signal 6


```

this one looks slightly worse.... :(

---

### Post by jdong on 2005-05-16
ubuntu-geek, when you get a chance, can you set up a cron job (at like 1 hour intervals) to run /home/jdong/sync_repo.sh ?

---

