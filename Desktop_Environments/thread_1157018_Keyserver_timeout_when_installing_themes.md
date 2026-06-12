---
title: "Keyserver timeout when installing themes"
date: 2009-05-12
forum: Desktop Environments
---

### Post by jdenhaan on 2009-05-12
Hi all,

Searched the forums but couldn't find any related threads, so I'll start one myself.

I've been trying to install the Gnome Themes mentioned in [this post]("http://webupd8.blogspot.com/2009/05/9-great-gnome-themes-with-ubuntu.html"), but when I follow the instructions given I run into trouble when trying to add the proper keys.

The command:
> sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0x1781bd45c4c3275a34bb6aec6e871c4a881574de

Quits on me with the following messages:
> Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 0x1781bd45c4c3275a34bb6aec6e871c4a881574de
gpg: requesting key 881574DE from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

In the comments below the post it is suggested that the server might be temporarily down, but after a few days of trying a few times a day (and seemingly being the only one still affected), I'm wondering if this is really the case.

Does anyone know whether the keyserver has been down for a while or not? And if not (which I think is the case, since I can't find any news on these servers being down), could anyone help me in solving this issue? Is it a firewall problem of some sorts? I see pinging the server works fine, but approaching it in my browser times out as well...

Thanks,

Jeroen

---

### Post by sushrutshirole on 2009-05-26
i am having same issue :( ](*,) .. i have set http_proxy n checked firewall .. still its giving time out error .. any idea?? (me too using jaunty)

---

