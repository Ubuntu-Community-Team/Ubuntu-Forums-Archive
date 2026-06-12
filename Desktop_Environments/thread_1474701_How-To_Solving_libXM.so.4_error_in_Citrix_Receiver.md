---
title: "How-To: Solving libXM.so.4 error in Citrix Receiver (ICAClient) on Ubuntu"
date: 2010-05-06
forum: Desktop Environments
---

### Post by swamytk on 2010-05-06
I have made small how-to on solving missing libXm.so.4 error in Ubuntu 10.04.

```
$ /usr/lib/ICAClient/wfcmgr -icaroot /usr/lib/ICAClient
/usr/lib/ICAClient/wfcmgr: error while loading shared libraries: libXm.so.4: cannot open shared object file: No such file or directory
```

Continue reading here: [http://karuppuswamy.com/wordpress/2010/05/06/how-to-solving-libxm-so-4-error-in-citrix-receiver-icaclient-on-ubuntu/](http://karuppuswamy.com/wordpress/2010/05/06/how-to-solving-libxm-so-4-error-in-citrix-receiver-icaclient-on-ubuntu/)

---

### Post by minja on 2013-01-20
Hi,
you shold install libmotif4:

# apt-get install libmotif4

---

