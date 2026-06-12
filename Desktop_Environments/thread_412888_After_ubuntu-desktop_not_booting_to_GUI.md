---
title: "After ubuntu-desktop not booting to GUI"
date: 2007-04-18
forum: Desktop Environments
---

### Post by ericamcampbell on 2007-04-18
I did a aptitude update and then pulled in ubuntu-desktop but when I reboot it is not coming up in the gui - what do I do???

---

### Post by taurus on 2007-04-18
What happens when you run this command after you log in?

```
sudo /etc/init.d/gdm start
```

---

