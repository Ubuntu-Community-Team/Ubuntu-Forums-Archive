---
title: "Problems with fusion"
date: 2007-06-23
forum: Desktop Effects &amp; Customization
---

### Post by Schnare on 2007-06-23
ok I'm hoping that I've just done something wrong but after I install compiz and do the whole alt+F2 compiz --replace nothing happens
 or I get this: Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

I seriously hope I've just done something wrong and that it is possible to run
am I just completely screwed?

---

### Post by isaacj87 on 2007-06-23
I saw something related to that on the Compiz Fusion website...I'll give you the link: [http://forums.opencompositing.org/viewtopic.php?f=12&t=878]("http://forums.opencompositing.org/viewtopic.php?f=12&t=878")

I hope that helps...tell me if it doesn't and I'll try to find something else. As far as I know, there's not alot a support for Compiz Fusion...still brand new I guess..but I'm having startup problems with it.

---

### Post by Schnare on 2007-06-23
I found out on another thread that it should work
I do have the pixmap support but it doesn't want to work for me
thanks though

---

### Post by Schnare on 2007-06-23
I found out on another thread that it should work
I do have the pixmap support but it doesn't want to work for me
thanks though

---

### Post by 9a3eedi on 2007-06-25
I assume that you are using ATI cards

Are you sure that you have DRI working?

```
fglrxinfo 
```

and are you sure you managed to configure XGL and start an XGL session?

---

