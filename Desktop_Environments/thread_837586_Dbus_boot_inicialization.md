---
title: "Dbus boot inicialization"
date: 2008-06-22
forum: Desktop Environments
---

### Post by eduf.santos on 2008-06-22
Hello guys, i accidentally disable from Admin > Services the dbus. Now everytime i log in i need to start it manually via ```
sudo /etc/init.d/dbus start
```

When i do this, i can access again the Services menu but the unlock button is disablen then i cant enable it via this panel. I would like to know how can i do it via terminal or just make the unlock button enable so i can enable the DBUS service again.

Can someone help me please?

PS:. My Ubuntu version is Hardy

---

### Post by ebash on 2008-06-23
You can enable the DBus service manually with the following command in a shell:

```
sudo ln -s /etc/init.d/dbus /etc/rc2.d/S12dbus
```

Of course this change will only take effect at the next reboot.

---

### Post by eduf.santos on 2008-06-23
Thank you very much. As sas i get home, i´ll try it :)

I´ll post the result here!

---

