---
title: "Titlebar on windows missing"
date: 2011-11-23
forum: Desktop Environments
---

### Post by idinium on 2011-11-23
Hi,
I have recently updated my ubuntu to 11.10 and from the update i can no longer see titlebars. Before the update iwas using Compiz to manage this stuff but since it doesnt wok with 11.10 version i dont know what to do. I tried metacity --replace command and it gets the titlebar back but only until i close terminal + it crashes the whole system and i need to restart the comp. After restart the problem is still there. Pls help....

---

### Post by BC59 on 2011-11-23
As I understand you should reset Compiz before upgrading the system.

Now go here to see if this helps reseting Unity and Compiz

[http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html](http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html)


If not you should uninstall Compiz but we are going too far this way.

```
sudo apt-get autoremove --purge compiz* libcompiz* libdeco* emerald* libemerald*
```

---

### Post by idinium on 2011-11-23
Thx so much :D works like a charm now , just needed the reset :P

---

