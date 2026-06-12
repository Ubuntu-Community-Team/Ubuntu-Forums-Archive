---
title: "Swiftfox and plugins"
date: 2006-06-02
forum: Desktop Environments
---

### Post by GQed76 on 2006-06-02
I have installed both Java and Flash.  It works in opera, but not Swiftfox.  Swiftfox is saying no plugins are installed.

---

### Post by aysiu on 2006-06-02
How did you install Swiftfox?

---

### Post by GQed76 on 2006-06-02
follwed these directions

[http://www.ubuntuforums.org/showthread.php?t=142798&highlight=swiftfox](http://www.ubuntuforums.org/showthread.php?t=142798&highlight=swiftfox)

---

### Post by aysiu on 2006-06-02
If you followed these directions: ```
cd /path/to/your/homefolder/swiftfox/plugins/
sudo ln -s /usr/lib/mozilla-firefox/plugins/* .
``` it may not work (that's the Breezy location). I believe Dapper moved the plugins to */usr/lib/firefox/plugins*.

So you would ```
cd ~/swiftfox/plugins
ls
sudo ln -s /usr/lib/firefox/plugins* .
ls
``` As the instructions stated, though, **don't forget the period at the end of that line**.

---

### Post by GQed76 on 2006-06-03
bah, still didnt work

---

### Post by donar73 on 2006-06-03
This worked for me:

```
cd /opt/swiftfox/plugins/
sudo ln -s /usr/lib/mozilla-firefox/plugins/*
```

---

