---
title: "how to install firefox dom inspector?"
date: 2006-09-01
forum: Desktop Environments
---

### Post by jimmyp on 2006-09-01
I am running dapper and can't figure out how to install the firefox dom inspector.

The generic answer is to reinstall firefox and choose to install the inspector but I'm trying to stick with software from the repositories. So if I install firefox with apt, it doesn't ask whether I want the inspector or not.

From the repository doesn't work:
sudo apt-get install firefox-dom-inspector

The following packages have unmet dependencies:
firefox-dom-inspector: Depends: firefox (= 1.5.dfsg+1.5.0.3-0ubuntu3) but 1.5.dfsg+1.5.0.5-0ubuntu6.06.1 is to be installed
E: Broken packages

Next, I hear you can install it by installing adt.xpi, but at 1.5.0.5, there is no more adt.xpi in the directory:
[http://ftp-mozilla.netscape.com/pub/...linux-i686/xpi](http://ftp-mozilla.netscape.com/pub/...linux-i686/xpi)

There is one for 1.5.0.4, but when I try to install that, I get an error.

How do I install it?

Thanks.

---

### Post by celloandy on 2006-09-01
Looks like maybe you're trying to install versions from different repositories.  My version of firefox-dom-inspector depends on the newer version, there, and both come from the dapper-security repo.  Try making sure that your dapper-security repository is enabled in /etc/apt/sources.list, and that your package listing is up to date ("sudo apt-get update").

Andrew

---

### Post by jimmyp on 2006-09-01
I love you man.

I had to add universe and multiverse to this line:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse


Thanks a lot.

---

