---
title: "synaptic package reloader errors"
date: 2006-01-17
forum: General Help
---

### Post by iand675@gmail.com on 2006-01-17
I enabled universe and multiverse and when reloaded the packages, I got the following output:
```

W: GPG error: http://us.archive.ubuntu.com breezy-updates Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com breezy Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com breezy-backports Release: Unknown error executing gpgv
W: GPG error: http://security.ubuntu.com breezy-security Release: Unknown error executing gpgv
```

What's going on with synaptic?

---

### Post by Maggot on 2006-01-17
I got those too. I took out the country code in the very front.. ca for me (us for you) had no problems since.

---

### Post by iand675@gmail.com on 2006-01-17
how would you go about editing that?

---

### Post by lucidite on 2006-01-18
To edit that, you need to go to your sources.list - you need to type:
```

sudo gedit /etc/apt/sources.list
```

and you modify the links. (BTW, if you're like me, I'd suggest making a backup of your file before making any modifications...  :))
Don't know about the modifications Maggot suggested, however I had a similar problem when I was adding repositories & I followed the advice on this page
([http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)) & everything worked.

Hope this helps!

---

