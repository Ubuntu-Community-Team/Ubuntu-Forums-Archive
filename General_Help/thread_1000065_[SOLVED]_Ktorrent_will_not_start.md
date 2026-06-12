---
title: "[SOLVED] Ktorrent will not start"
date: 2008-12-02
forum: General Help
---

### Post by 16777216 on 2008-12-02
I get this error.

```
QFSFileEngine::open: No file name specified
ktorrent: symbol lookup error: /usr/lib/kde4/ktinfowidgetplugin.so: undefined symbol: _ZN18KSqueezedTextLabel5clearEv
<unknown program name>(17071)/: Communication problem with  "ktorrent" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" "
```

---

### Post by binbash on 2008-12-02
I guess there is a problem with info widget plugin.

Choose one of them : 

1- Delete your ktorrent configuration
2- sudo apt-get purge ktorrent and then install it again.

---

### Post by 16777216 on 2008-12-02
My greatest thanks to you binbash, no one on IRC nor in my previous post would even guess at my problem.
( Though I should have seen it myself. *smacks forehead* )

Option 1 did not work.
Option 2 however did!
I purged Ktorrent then recompiled it from source. (3.2 &#946;1)
Again, many thanks to you.

---

