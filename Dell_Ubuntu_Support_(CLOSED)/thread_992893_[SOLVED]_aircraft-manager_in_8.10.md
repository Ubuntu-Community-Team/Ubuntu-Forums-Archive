---
title: "[SOLVED] aircraft-manager in 8.10?"
date: 2008-11-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ytsejam1138 on 2008-11-25
Can someone explain to me how to get aircraft-manager installed in Ubuntu 8.10 It's not in the repositories and I'm unable to add the Dell Hardy repos. I downloaded the tarball but when I run 'sudo python setup.py install' I get a bunch of portio errors and it doesn't install.

I did have this running in 8.10, but after I did a reinstall last night, I cannot for the life of me figure out how to get it installed again.

If someone could point me to a .deb of aircraft-manager I would appreciate it.

[SOLUTION]
I finally figured this one out.

Download this aircraft-manager .deb [aircraft-manager](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/universe/binary-lpia/aircraft-manager_belmont11_all.deb)

Now in terminal navigate to the folder with the file and type:

```
sudo dpkg -i aircraft-manager_belmont11_all.deb
```

This will put an application in System>Preferences called Airplane Mode

---

