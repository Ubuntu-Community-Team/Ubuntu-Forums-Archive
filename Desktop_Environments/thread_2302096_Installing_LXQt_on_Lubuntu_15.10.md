---
title: "Installing LXQt on Lubuntu 15.10"
date: 2015-11-07
forum: Desktop Environments
---

### Post by paeschli on 2015-11-07
Hello everyone :)

So, we've been talking about LXQt since 13.04 was released and the original plan was for LXQt to be the new DE for 14.04 LTS ... Yeah, that didn't turn out very well.

Since it seems like the latest daily builds for 16.04 are still based on LXDE, I'd like to give LXQt a spin on 15.10 (especially since LXQt 0.10 was released a few days ago).

But a message was post in the mailing list saying that a few changes have been made to the LXQt PPA [https://lists.launchpad.net/lubuntu-qa/msg05383.html](https://lists.launchpad.net/lubuntu-qa/msg05383.html)

What do I need to do to install LXQt? Will a simple ```
sudo apt-get install lxqt-metapackage
``` do the trick?

Also, will it install LXQt 0.10 or are the repo's still on a 0.9.x version?

TIA

---

### Post by grahammechanical on 2015-11-07
> Work continues on integrating [LXQt]("http://lxqt.org/") into Lubuntu, but we'll likely not see it released until 16.10 (Y cycle). If you're curious about development, check out the [blueprints]("https://blueprints.launchpad.net/ubuntu/+spec/topic-v-flavor-lubuntu"). 


[LIST]
[*]There is a [prototype of Lubuntu with LXQT]("https://lists.ubuntu.com/archives/lubuntu-users/2014-October/008662.html") (aka [lubuntu-next]("https://launchpad.net/lubuntu-next")) available. Info and instructions from the boss included. 


[*]LXQt can also be installed on an existing system by installing [lxqt-metapackage]("https://bazaar.launchpad.net/%7Elubuntu-dev/lxde/lxqt-metapackage/view/head:/debian/control") from the [lubuntu-daily PPA]("https://launchpad.net/%7Elubuntu-dev/+archive/ubuntu/lubuntu-daily"). 

[URL="https://wiki.ubuntu.com/Lubuntu/Testing"]
https://wiki.ubuntu.com/Lubuntu/Testing[/URL]

Regards.

[/LIST]

---

### Post by paeschli on 2015-11-07
Thanks, I should have read the documentation first.

Seems like the version in the repositories is still 0.9 from what I can tell so I'll hold off for now.
```
paeschli@paeschli-desktop:~$ apt-cache show lxqt-metapackage | grep Version
Version: 0.0.1+bzr62+**20151023**0946~ubuntu15.10.1
```

---

