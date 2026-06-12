---
title: "tomboy cannot load"
date: 2009-10-16
forum: Desktop Environments
---

### Post by afeasfaerw23231233 on 2009-10-16
tomboy doesn't appear on the panel but ps -A show 4 tomboy processes are running. Any idea? 

Thanks in advance.

---

### Post by ajgreeny on 2009-10-16
You need the notification area on your panel for the icon to show.  Perhaps you need to add that by right clicking.  I am not sure about the indicator applet, which I think is supposed to take the place of notification area, as I don't use it, but maybe tomboy should show there as well.

---

### Post by afeasfaerw23231233 on 2009-10-17
Nothing happens when I right click on the panel > Add to Panel > Tomboy notes

---

### Post by vinutux on 2009-10-17
```
killall tomboy
```

Alt+F2 tomboy

---

### Post by afeasfaerw23231233 on 2009-10-17
> **vinutux said:**
> ```
killall tomboy
```

Alt+F2 tomboy

After running **killall tomboy**, tomboy is still here. tomboy can only be killed by **kill -15 tomboy**

ps -A |grep tomboy showed tomboy was running when the computer was booted up, but the tomboy icon didn't appear on the panel bar
```

ps -A |grep tomboy
 3647 ?        00:00:02 tomboy

```

Everytime I shutdown the computer there's a pop-up message saying tomboy is running.

---

