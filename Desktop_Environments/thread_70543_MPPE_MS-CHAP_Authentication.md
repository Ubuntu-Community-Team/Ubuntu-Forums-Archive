---
title: "MPPE MS-CHAP Authentication"
date: 2005-09-30
forum: Desktop Environments
---

### Post by Markpy on 2005-09-30
Hi, I have installed pptp-linux and setup a VPN connection but when I dial in using **pon** (with debugging options) I receive:

```
...
MPPE required, but MS-CHAP[v2] auth not performed.
sent [LCP TermReq id=0x2 "MPPE required but not available"]
rcvd [LCP TermReq id=0x3 "peer refused to authenticate"]
Connection terminated.
...
```

My **/etc/ppp/chap-secrets** file has my login details all setup and I have quoted and unquoted my password just incase that was a problem, why is it not performing the MS-CHAP authentication? **lsmod** shows that ppp_mppe is loaded.

???

---

### Post by mlomker on 2005-09-30
I'll be curious if anyone has gotten this to work on linux.  I did some experimentation when I was running Linspire and the only way that I could get it to work was to disable all encryption on my RAS server...kind of defeats the point, of course.

---

### Post by EmmEff on 2005-09-30
Hmmm...  I following the docs at the [Poptop]("http://www.poptop.org") website along with installing the pptp-linux client and everything worked out of the box.  I was pleasantly surprised to see that I didn't need to patch the kernel for mppe support.

I am running kernel 2.6.10-5.386 as well as pptp-linux 1.5.0-4 and ppp 2.4.2+20040428.  My pptp server is running the same.

---

