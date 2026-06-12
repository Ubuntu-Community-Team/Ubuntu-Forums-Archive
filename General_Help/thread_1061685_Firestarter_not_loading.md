---
title: "Firestarter not loading"
date: 2009-02-06
forum: General Help
---

### Post by pfwd.tech on 2009-02-06
Hi,
All of a sudden I am unable to load firestarter.
From the command line i get this error ```
External network device (null) is not ready Aborting..
```
A dialog box also appears and says the device eth0 is not ready please check your network settings and make sure your Internet connection is active.

I haven't changed any network setting.
Anyone konw what may be the issue and how to reslove it.

Thanks

---

### Post by hyper_ch on 2009-02-06
why do you want to start it anyway?

---

### Post by brian_p on 2009-02-06
> **pfwd.tech said:**
> 

I haven't changed any network setting.
Anyone konw what may be the issue and how to reslove it.

```
sudo ifconfig -a
```

Then try them in firestarter one by one.

---

### Post by pfwd.tech on 2009-02-07
I've managed it.  I ran the setup wizard in firestarter and it works fine on eth0.
Any one know how I can load this at boot? Its a pain having to click firestarter each time I log in
..Its a desktop machine if that makes any difference

I would mark this as solved but I cant see the link in thread tools

---

