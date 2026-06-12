---
title: "Java not working in Swiftfox??!"
date: 2009-01-23
forum: General Help
---

### Post by fugazi32 on 2009-01-23
Okay, I have Java running fine when I browse with Firefox, but when I use Swiftfox (an optimized version of Firefox, Google it) it says I don't have the Java Runtime Environment installed...any one got any answers? Help much appreciated.
:)

---

### Post by ibuclaw on 2009-01-23
The plugins for firefox are installed in a separate directory to swiftfox.

If you can locate where the swiftfox plugins are kept, then you can symlink the firefox plugins.

```
sudo ln -s /usr/lib/firefox/plugins **/location/of/swiftfox/plugins**
```

Regards
Iain

---

### Post by markharding557 on 2009-01-23
don't reckon much to swiftfox myself,could never tell any difference.
also i don't like the license it has

---

### Post by Earthen on 2009-07-30
sudo ln -s /usr/lib/firefox/plugins /usr/lib/swiftfox/plugins

this command did it for me just restart swiftfox before testing cause it killed X when I tried!  :-/

---

