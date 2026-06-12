---
title: "Issues with libssl.so libcrypto.so"
date: 2011-08-03
forum: Desktop Environments
---

### Post by ashesh0326 on 2011-08-03
```
/usr/bin/php: /usr/local/zend/lib/libssl.so.0.9.8: no version information available (required by /usr/bin/php)
/usr/bin/php: /usr/local/zend/lib/libcrypto.so.0.9.8: no version information available (required by /usr/bin/php)
```

Hi guys. I recently installed zend-framework and zend-server on my office desktop and ever since, I've been getting the above warning messages everytime I hit the tab for autocomplete on the shell (especially when using git) or when I run any random PHP file as script. Moreover, this problem breaks some stuff at times, for example, git GUI never works for me. And getting this warning everytime is downright annoying as well.

From the looks of it, the Zend installation somehow messed up my linkages. I'd like to know how to fix this. Any help?

---

### Post by rchaplin on 2011-09-23
It's not a solution, but rather a workaround. Kervin Ramen states in his [blog post]("http://blog.kervinramen.com/2011/06/zend-server-with-ssh-libcrypto-libssl.html") that if you simply rename the offending shared objects, it at least stops failing.

```

sudo mv /usr/local/zend/lib/libssl.so.0.9.8 /usr/local/zend/lib/libssl.so.0.9.8.hold

sudo mv /usr/local/zend/lib/libcrypto.so.0.9.8 /usr/local/zend/lib/libcrypto.so.0.9.8.hold

```

HTH

---

