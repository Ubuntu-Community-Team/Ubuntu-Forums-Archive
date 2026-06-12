---
title: "problem after upgrade on 8.10"
date: 2009-05-11
forum: General Help
---

### Post by muctadir on 2009-05-11
i upgraded my ubuntu 8.10. after upgrade there is two option for ubuntu in os choice menu.

what can i do to remove the previous one????

---

### Post by trentscott4 on 2009-05-11
You should be able to edit the GRUB config file. From terminal: 

```
sudo vi /boot/grub/menu.lst
```

Check this out for more info:
[http://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/configure-boot-loader-grub.html](http://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/configure-boot-loader-grub.html)

---

### Post by Zoowey on 2009-05-11
> **muctadir said:**
> i upgraded my ubuntu 8.10. after upgrade there is two option for ubuntu in os choice menu.

what can i do to remove the previous one????

You can use a utility program called Ubuntu Tweak to easily get rid of the old kernel.

Simply install Ubuntu Tweak, launch it, click on "applications" then "package cleaner." It will have an option called "clean kernel" which will rid you of any old kernels.

[http://www.getdeb.net/release.php?id=4324](http://www.getdeb.net/release.php?id=4324)

---

### Post by geraldvillorente on 2009-05-11
edit the /boot/grub/menu.lst
```

vim /boot/grub/menu.lst

```

---

