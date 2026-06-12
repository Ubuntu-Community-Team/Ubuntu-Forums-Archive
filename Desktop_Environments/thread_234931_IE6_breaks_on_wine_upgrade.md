---
title: "IE6 breaks on wine upgrade"
date: 2006-08-12
forum: Desktop Environments
---

### Post by frogotronic on 2006-08-12
Upgrading wine to 0.9.18 or 0.9.19 breaks ie6.  Any patches or ways to regress back to 0.9.5?

Thanks

---

### Post by jordilin on 2006-08-12
How have you installed wine? I have version 0.9.9 from ubuntu official Dapper repos.

---

### Post by frogotronic on 2006-08-12
yep, I used this howto [HTML]http://www.ubuntuforums.org/showthread.php?t=149585&highlight=internet+explorer[/HTML] to install everything and it worked.  Then I upgraded to 0.9.19 and everything but ie6 works.  ie6 just opens a windown labelled WINE INTERNET EXPLORER and then nothing appears in the blank window.

---

### Post by jordilin on 2006-08-12
I followed the howto:
[http://jordilin.wordpress.com/2006/07/16/internet-explorer-under-ubuntu/](http://jordilin.wordpress.com/2006/07/16/internet-explorer-under-ubuntu/)
and works flawlessly.
Try to install the internet explorer pointed out in the howto.

---

### Post by den_ on 2006-08-12
I supose you can simply remove your current wine version remove wine directory in your home dir (rm -r .wine) and install again the version which you want. also reinstall wt and install it again. the same procedure. where is the problem?

You can also have ie6 with newer versions of wine with ie4linux script.

[http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html)

---

