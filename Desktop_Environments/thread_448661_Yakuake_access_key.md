---
title: "Yakuake access key"
date: 2007-05-19
forum: Desktop Environments
---

### Post by thelinuxguy on 2007-05-19
I changed the yakuake access key. I made some mistake and now I don't know what the key is. When yakuake starts, a notification at the upper left corner says something like 'yakuake started successfully, use <blank here> key to access it'. It shows a blank where the key should be. Space and Tab do not work. F12 and my previous access key don't work either. So now I have yakuake running in the background but no key to access it.

How can I change the access key without yakuake showing up?

---

### Post by thelinuxguy on 2007-05-22
Solved. I had to add the following to ~/.kde/share/config/yakuakerc

```

[Global Shortcuts]
AccessKey=Alt+A

```

I have no idea how it had disappeared from the config file. The page at [http://people.ubuntu.com/~fabbione/irclogs/archived/2006-06/kubuntu-devel-2006-06-24.html](http://people.ubuntu.com/~fabbione/irclogs/archived/2006-06/kubuntu-devel-2006-06-24.html) (search for AccessKey=Alt+A) helped.

Thanks.

---

### Post by thelinuxguy on 2007-05-22
Marked thread as resolved.

---

