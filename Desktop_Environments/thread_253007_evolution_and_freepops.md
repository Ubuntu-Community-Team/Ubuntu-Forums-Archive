---
title: "evolution and freepops"
date: 2006-09-07
forum: Desktop Environments
---

### Post by piero1989 on 2006-09-07
I have a problem with evolution and freepos
When I start with downloading the email I see the message
 "Unable to connect to POP server localhost.
  Error sending password: Operazione ora in corso"

I have set pop = localhost:2000 and the freepops server seem to work

Please help me

Piero

---

### Post by makadam on 2006-10-26
Hello

I resolved my problem by installing the freepops init script with this command:
```
sudo update-rc.d freepops default
```

---

### Post by mir123 on 2006-10-27
I had to manually install the latest hotmail module from [http://www.freepops.org/en/viewplugins.php](http://www.freepops.org/en/viewplugins.php) in order to get it to work.

---

