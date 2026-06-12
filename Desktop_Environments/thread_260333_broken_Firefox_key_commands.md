---
title: "broken Firefox key commands"
date: 2006-09-18
forum: Desktop Environments
---

### Post by uturn on 2006-09-18
I'm running Dapper. It seems some key commands for firefox are broken, for example using alt-d to respond to a cookie dialog, or alt-n for Find Next. Anyone else have the same problem? Can anyone point me to a fix?

Thanks.

---

### Post by uturn on 2006-09-21
Fixed. In about:conifg set the value of ui.key.generalAccessKey to 18. Mine was 0, which disables the key. For more info, see:

[http://kb.mozillazine.org/Ui.key.generalAccessKey](http://kb.mozillazine.org/Ui.key.generalAccessKey)

---

