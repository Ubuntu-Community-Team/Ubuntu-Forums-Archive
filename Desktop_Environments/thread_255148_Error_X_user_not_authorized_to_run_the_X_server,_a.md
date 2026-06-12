---
title: "Error: X: user not authorized to run the X server, aborting."
date: 2006-09-11
forum: Desktop Environments
---

### Post by kaitlyn on 2006-09-11
Hello,

I've come to Ubuntu from Gentoo, and installed it today.  One thing I am trying to get working is 'View_on_Tv', a service menu that allows Nvidia cards to use TV out on an alternitive X server to show video media files.

When it didn't work, I found that when it tries to execute:

```

X -screen TV :1 -ac

```

the following error is returned:

```

X: user not authorized to run the X server, aborting.

```

Google has suggested a few things but none of them have worked, so I wanted to ask here.

---

### Post by kaitlyn on 2006-09-13
This error has been fixed,

The solution was:

```
sudo dpkg-reconfigure x11-common
```

1.  Select "Anyone" for who has permission to start the X server.
2.  Enter nice value ( 0 recommended, this is irrevelent to permissions, but you will be prompted.)

Major thanks goes to DanaG on #Ubuntu @ freenode who told me this.

---

### Post by patrick295767 on 2006-12-22
> **kaitlyn said:**
> This error has been fixed,

The solution was:

```
sudo dpkg-reconfigure x11-common
```

1.  Select "Anyone" for who has permission to start the X server.
2.  Enter nice value ( 0 recommended, this is irrevelent to permissions, but you will be prompted.)

Major thanks goes to DanaG on #Ubuntu @ freenode who told me this.

You can also give them too your sudo password :D :D It is not secured dude

---

