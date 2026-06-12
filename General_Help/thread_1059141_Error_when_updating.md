---
title: "Error when updating"
date: 2009-02-03
forum: General Help
---

### Post by alecspoons on 2009-02-03
I've just installed Wubi onto a Windows XP laptop without any problems. I've using Ubuntu for some time now and I am very familiar it. I can say that I am very happy with the way that Wubi allows me to use Ubuntu.

However, each time I start up, I have an update to do which will not work. It get so far and then shows the following message:

E: /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version

I've never experienced this on a purely-Ubuntu machine, so I don't know if it is Wubi-specific or something more Ubuntu general. Either way, I can't seem to get round it.

Anyone have any thoughts?

Thanks

---

### Post by icheyne on 2009-02-03
It's a Wubi bug - [https://bugs.launchpad.net/wubi/+bug/252900](https://bugs.launchpad.net/wubi/+bug/252900)

There are some workarounds listed in the bug report.

Try:
```

sudo aptitude update
sudo aptitude install linux-image-2.6.24-18-generic
sudo aptitude remove linux-image-2.6.27-7-generic
sudo aptitude upgrade

```

---

### Post by alecspoons on 2009-02-07
Thanks

I'll have a look at this and report back.

---

### Post by alecspoons on 2009-02-10
So - thanks again.

I tried this and it worked.
I gather from the Wubi bugs post you directed me to that it is an issue that occurs when you are upgrading from one subversion to another. After following your instructions, I actually had to do it again, but this time substitute different version numbers and that worked just fine as well.

Thanks again icheyne.

---

### Post by icheyne on 2009-02-10
Brilliant! Thanks for letting me know.

---

