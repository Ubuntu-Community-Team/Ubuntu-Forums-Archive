---
title: "How can I manually set the NetworkManager driver to use?"
date: 2006-06-11
forum: Desktop Environments
---

### Post by Vinze on 2006-06-11
Hey, I get the following output:

```
$ sudo NetworkManager --no-daemon
NetworkManager: <information>   starting...
NetworkManager: <WARNING>        main (): nm_data_new: Setting up dbus filter
NetworkManager: <information>   eth1: Device is fully-supported using driver 'pr ism54'.
```

As you can see, it says it uses driver "prism54", but as I've been messing with WPA some longer, I know it should be "hostap".

How can I manually set the driver?

---

