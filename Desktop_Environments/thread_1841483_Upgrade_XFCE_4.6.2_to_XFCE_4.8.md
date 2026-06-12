---
title: "Upgrade XFCE 4.6.2 to XFCE 4.8?"
date: 2011-09-09
forum: Desktop Environments
---

### Post by galacticaboy on 2011-09-09
I am using Xubuntu 10.10, I do not want to upgrade to 11.04 right now, but I do want to upgrade my XFCE from 4.6.2 to XFCE 4.8. How do I do that?

---

### Post by Toz on 2011-09-09
Have a look here: [http://www.webupd8.org/2011/01/xfce-48-ubuntu-1004-and-1010-ppas.html]("http://www.webupd8.org/2011/01/xfce-48-ubuntu-1004-and-1010-ppas.html")

---

### Post by galacticaboy on 2011-09-10
When I added PPA in the terminal it worked, but then I did 'sudo apt-get update' and I got this message,

'W: Failed to fetch [http://ppa.launchpad.net/koshi/xfce4.8/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/koshi/xfce4.8/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/koshi/xfce4.8/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/koshi/xfce4.8/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.'

??What is that??

---

### Post by Toz on 2011-09-10
Hmmmm. The files do exist.

[http://ppa.launchpad.net/koshi/ppa/ubuntu/dists/maverick/main/source/]("http://ppa.launchpad.net/koshi/ppa/ubuntu/dists/maverick/main/source/")

and

[http://ppa.launchpad.net/koshi/ppa/ubuntu/dists/maverick/main/binary-i386/]("http://ppa.launchpad.net/koshi/ppa/ubuntu/dists/maverick/main/binary-i386/")

Can you access these two web pages?

Maybe try it again:
```
sudo apt-get update
```

---

### Post by galacticaboy on 2011-09-10
> **Toz said:**
> Hmmmm. The files do exist.

[http://ppa.launchpad.net/koshi/ppa/ubuntu/dists/maverick/main/source/]("http://ppa.launchpad.net/koshi/ppa/ubuntu/dists/maverick/main/source/")

and

[http://ppa.launchpad.net/koshi/ppa/ubuntu/dists/maverick/main/binary-i386/]("http://ppa.launchpad.net/koshi/ppa/ubuntu/dists/maverick/main/binary-i386/")

Can you access these two web pages?

Maybe try it again:
```
sudo apt-get update
```

I got it, all I did was go into my Software Center, remove the PPA, then add it again and it works, as I type it is upgrading, thank you!

---

