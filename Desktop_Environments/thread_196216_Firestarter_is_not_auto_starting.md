---
title: "Firestarter is not auto starting"
date: 2006-06-13
forum: Desktop Environments
---

### Post by kpkeerthi on 2006-06-13
I have enabled Firestarter (sudo firestarter --start-hidden) under startup programs in Session properties but it won't start. I have enabled tray icon but can't see it. I had to manually start it each time I log in. Any ideas? Thanks.

---

### Post by bukwirm on 2006-06-13
I had a similar problem, what I wound up doing was 'gksudo firestarter', entering my password, then closing the firestarter window. This is not a great solution, but it works.

---

### Post by 23meg on 2006-06-13
You don't really need the Firestarter GUI to run on startup; by default it's active on startup even when the GUI isn't visible. To make sure, you can check its status with ```
sudo /etc/firestarter/firestarter.sh status
```

---

### Post by kpkeerthi on 2006-06-13
Super. Thanks a ton.  Its running...

---

### Post by kpkeerthi on 2006-06-13
OK... here is a pretty lame question. Please do not get annoyed for asking this. I'm a linux super-newbie. So here it goes...

Does firestarter require 'su' privileges? If yes, how can it start upon login without promting for su password? :confused:

---

### Post by kpkeerthi on 2006-06-13
[bump]
Can someone please clarify?

---

### Post by scxtt on 2006-06-13
yes, it's a GUI frontend to iptables - something not just any user should be able to "mess with" ...

---

