---
title: "Skype Qt Issue"
date: 2009-03-15
forum: General Help
---

### Post by lvleph on 2009-03-15
I have done some searching, but still can't seem to solve this issue.
I am getting the 
```
Fatal: Cannot mix incompatible Qt libraries
Aborted
```
error

The result of 
```

ldd /usr/bin/skype | grep -i qt
	libQtDBus.so.4 => /usr/lib/libQtDBus.so.4 (0xf7dce000)
	libQtGui.so.4 => /usr/lib/libQtGui.so.4 (0xf74cb000)
	libQtNetwork.so.4 => /usr/lib/libQtNetwork.so.4 (0xf73ca000)
	libQtCore.so.4 => /usr/lib/libQtCore.so.4 (0xf719c000)
	libQtXml.so.4 => /usr/lib/libQtXml.so.4 (0xf6db9000)

```

Everything looks fine, but nothing I still get the error.

---

### Post by dusan.saiko on 2009-03-15
How did you install the Skype ?

I am using Medibuntu repositories and it works quite fine for me.
If you have still a problem with shared libraries, try to use skype-static version from repository. See  [http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by lvleph on 2009-03-16
I ended up upgrading to 8.10 and now it works.

---

