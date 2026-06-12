---
title: "GPG error"
date: 2009-06-05
forum: General Help
---

### Post by yonyz on 2009-06-05
Whenever I run the 'sudo apt-get update' command, I get the GPG error that can be seen in the attached screenshot.

How can I fix it?

[IMG]http://i41.tinypic.com/2zioffk.png[/IMG]

---

### Post by bacardiandwatermelon on 2009-06-05
A quick search of the forums should have brought up this command...
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <key id>
```

---

### Post by binbash on 2009-06-05
[http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html](http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html)

---

### Post by yonyz on 2009-06-06
> **bacardiandwatermelon said:**
> A quick search of the forums should have brought up this command...
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <key id>
```

"bash: syntax error near unexpected token `newline'".

binbash: It worked. Thank you.

---

