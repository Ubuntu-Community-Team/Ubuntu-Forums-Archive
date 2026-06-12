---
title: "Beagle issue"
date: 2005-08-05
forum: Desktop Environments
---

### Post by Aragorn992 on 2005-08-05
"Corlib not in sync with this runtime: expected corlib version 37, found 22.
Download a newer corlib or a newer runtime at http://www.go-mono.com/daily."

This is the error I get often when trying to run lots of the beagle scripts, any adivce?

---

### Post by dave84 on 2006-01-16
sorry for being so late!

i recommend to download the lateset mono you can get and install it first.
if the problem remains:

1) download from a mono mirror the correct monolite-package
2) extract the files:
```
tar xvzf monolite-xxxxxxxx
```
3) copy the files into your mono-directory:
in my case:
```
cd monolite-xxxxxxxx;
cp * /opt/lib/mono/2.0/
```

ps: your PATH variable should point to the correct directory too.

---

