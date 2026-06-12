---
title: "NODM (display manager) doesn't start X in my system."
date: 2014-09-20
forum: Desktop Environments
---

### Post by fernando29 on 2014-09-20
Hi.


I am seting up a kiosk system, so I followed [this]("http://nexxylove.tumblr.com/post/22690398464/ubuntu-web-kiosk-in-10-easy-steps") tutorial, where it is given the instruction for, starting from a "text only" system (I used a Lubuntu Minimal), to set up a kiosk by installing xorg and nodm. 


Now, all went well with xorg. If I run:


```
$ startx
```


my ~/.xsession file get executed (I am using leafpad only as a simple test):


```

#!/usr/bin/env bash
echo "something" > /root/someFile
leafpad

```


but when I boot the system, all I got is a black screen and "/root/someFile" is not even created. It is supposed that nodm should trigger an XSession, but something is happening. My /etc/default/nodm is:


```
NODM_ENABLED=true


NODM_USER=root


NODM_FIRST_VT='7'


NODM_XSESSION=/etc/X11/Xsession


NODM_X_OPTIONS='-nolisten tcp'


NODM_MIN_SESSION_TIME=60
```


I have tried with a different (non root) user too, but the result is the same.


If I run:


```
$ nodm
```


X is started and /root/someFile is created.


I hope somebody could give me some help in this regard. Thanks.

---

### Post by ibjsb4 on 2014-09-21
Your link is 404 (broke).

Have you edited /etc/X11/default-display-manager to include nodm?  It should read like this:
```
/usr/sbin/nodm
```

---

### Post by fernando29 on 2014-09-30
> **ibjsb4 said:**
> Your link is 404 (broke).

Have you edited /etc/X11/default-display-manager to include nodm?  It should read like this:
```
/usr/sbin/nodm
```

Hi ibjsb4.

Thanks for your response. I fixed the link. Regarding my initial problem, I got an alternative solution, by using "rungetty" instead nodm. mingetty lets you auto login with the user you want, and then launch X (startx) or the program you want from /root/.bash_profile file.

---

