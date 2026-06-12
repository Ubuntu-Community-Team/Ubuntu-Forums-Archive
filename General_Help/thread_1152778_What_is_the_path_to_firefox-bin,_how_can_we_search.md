---
title: "What is the path to firefox-bin, how can we search"
date: 2009-05-08
forum: General Help
---

### Post by tharindufit on 2009-05-08
Hi,

I am trying to write program that needs path to firefox-bin. I am using ubuntu 9.04. /usr/lib/firefox-3.0.10 but inside that there is no file named firefox-bin. Where can I find this file. I am not sure if this is the right place to post this. But I kindly appreciate if someone could point me some way to look for this. At least some way to search perhaps.

Kind regards,
-Tharindu

---

### Post by amac777 on 2009-05-08
You can try these commands to search for it:

```
whereis firefox-bin
```

```
locate firefox-bin
```

or if those don't give you the answer:

```
find / -name 'firefox-bin'
```

---

