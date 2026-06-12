---
title: "vsftpd problem"
date: 2009-04-02
forum: General Help
---

### Post by ronin2307 on 2009-04-02
total newbie here so I managed to do something stupid I think.
I am trying to set up vsftpd, and after two days of messing with it I wanted to start over from scratch. so i uninstalled vsftpd using

sudo apt-get remove vsftpd

however I still had the vsftpd.conf file in the /etc folder. thinking it was a remnant I manually removed it because I wanted a fresh default file when I reinstall.
to my surprise that didn't happen.
so my question is how do I create a default vsftpd.conf file?

thanks

---

### Post by 3Miro on 2009-04-02
Try:
```
sudo apt-get purge vsftpd

```

---

### Post by kanikilu on 2009-04-02
If all you want is that one file, you could just download the source manually, and it has the conf file in there:

[http://archive.ubuntu.com/ubuntu/pool/main/v/vsftpd/vsftpd_2.0.7.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/v/vsftpd/vsftpd_2.0.7.orig.tar.gz)

---

### Post by ronin2307 on 2009-04-02
3Miro
that did the trick. many thanks

could you explain to me why remove didn't work? why the the apt-get install think that the file was still there?


thanks

---

### Post by ronin2307 on 2009-04-02
kanikilu,
thanks for that advice as well. something I will keep in mind for future mistakes

---

### Post by kanikilu on 2009-04-02
Remove didn't work because it retains configuration files. Purge removes the application *and* configuration files.

---

### Post by ronin2307 on 2009-04-02
where do these files reside?
Remember, I manually deleted the vsftpd.conf file

---

