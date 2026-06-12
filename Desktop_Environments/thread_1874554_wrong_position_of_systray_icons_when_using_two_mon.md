---
title: "wrong position of systray icons when using two monitors"
date: 2011-11-03
forum: Desktop Environments
---

### Post by yarozar on 2011-11-03
Ubuntu 32bit v11.10, Unity.

I am using external big monitor (1920x1080) connected to my laptop (1366x768). Using TwinView screens, big is to the right from small. As primary I have set the big one, though Launchbar is still on left most (small)

There is incorrect position of systray icons on the big monitor:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=206217&stc=1&d=1320328022[/IMG]

There is no issue with systray icons placement when I work only with the small screen and they are correctly aligned to the right.

Let me know what is the best way to fix it or report whoever understands and knows the procedure.

Thanks!

---

### Post by mjuhasz on 2011-11-03
The launcher is not respecting the primary screen option and it's always on the leftmost screen. There is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/742544") about it, and a PPA exists with a patch which has not made its way into the unity yet.
The PPA is here: [https://launchpad.net/~vanvugt/+archive/unity/](https://launchpad.net/~vanvugt/+archive/unity/)
or you can just type:

```
sudo add-apt-repository ppa:vanvugt/unity
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by mjuhasz on 2011-11-03
The notification area position is calculated incorrectly for dual screens. The [bug report]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/778256") has a [fix]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/778256/comments/12") but you have to rebuild unity by yourself which is not a walk in the park unless you are familiar with command line and building deb packages.

BTW, one of the main goal for 12.04 is improved multiscreen support.

---

