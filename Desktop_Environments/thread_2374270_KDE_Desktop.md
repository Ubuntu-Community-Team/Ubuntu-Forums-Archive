---
title: "KDE Desktop"
date: 2017-10-14
forum: Desktop Environments
---

### Post by kan1969 on 2017-10-14
Hi Experts,

I have installed KDE Plasma Desktop as per the instructions from this website: "https://www.tecmint.com/install-kde-plasma-5-in-linux/".

It ended with errors: "Errors were encountered while processing: /tmp/apt-dpkg-install-Wg4UUM/635-kaccounts-providers_4%3a16.04.3-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)5".

To have a better picture of it, I am posting it from where it started.

```

Selecting previously unselected package kaccounts-providers.
Preparing to unpack .../635-kaccounts-providers_4%3a16.04.3-0ubuntu1_amd64.deb ...
Unpacking kaccounts-providers (4:16.04.3-0ubuntu1) ...
dpkg: error processing archive /tmp/apt-dpkg-install-Wg4UUM/635-kaccounts-providers_4%3a16.04.3-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/etc/signon-ui/webkit-options.d/accounts.google.com.conf', which is also in package account-plugin-google 0.13+16.10.20160929.1-0ubuntu1
Selecting previously unselected package kde-config-whoopsie.
Preparing to unpack .../636-kde-config-whoopsie_15.10ubuntu2_amd64.deb ...
Unpacking kde-config-whoopsie (15.10ubuntu2) ...
Selecting previously unselected package kio-mtp.
Preparing to unpack .../637-kio-mtp_0.75+git20140304-2_amd64.deb ...
Unpacking kio-mtp (0.75+git20140304-2) ...
Selecting previously unselected package oxygen5-icon-theme.
Preparing to unpack .../638-oxygen5-icon-theme_5%3a5.34.0-0ubuntu1~ubuntu16.10~ppa1_all.deb ...
Unpacking oxygen5-icon-theme (5:5.34.0-0ubuntu1~ubuntu16.10~ppa1) ...
Selecting previously unselected package skanlite.
Preparing to unpack .../639-skanlite_2.0-1_amd64.deb ...
Unpacking skanlite (2.0-1) ...
Errors were encountered while processing:
 /tmp/apt-dpkg-install-Wg4UUM/635-kaccounts-providers_4%3a16.04.3-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Kindly help me with your solutions.

With Kind Regards,
Kan1969

---

### Post by entw on 2017-10-14
```
sudo dpkg -r account-plugin-google
sudo apt-get -f install
```

---

### Post by kan1969 on 2017-11-01
Hello ENTW,

Thanks for your solution - it worked!

Kannan

---

### Post by vasa1 on 2017-11-01
[How to mark threads [SOLVED] or [UNSOLVED]](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

