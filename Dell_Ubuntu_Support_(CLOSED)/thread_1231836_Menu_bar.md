---
title: "Menu bar"
date: 2009-08-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Greasy_Larry on 2009-08-05
I recently add Ubuntu 9.04 as the second os. I did not like the desktop environment, so I changed it to the basic one. Now I can't see the menu bar or task bar. I basically have a desktop background viewer. Does anybody know the shortcut keys to open up the system dropdown menu, or know how to aleviate this headache. Oh, this is on a Dell Mini 10v.

---

### Post by mikewhatever on 2009-08-05
Can you explain what's the 'basic one' as opposed to the desktop environment? Just guessing here, but have you installed the UNR (Ubuntu Netbook Remix) and then switched to the regular looking Ubuntu? What's the deal with the menu and task bar? Can you see the top and bottom panels?

---

### Post by Greasy_Larry on 2009-08-05
> **mikewhatever said:**
> Can you explain what's the 'basic one' as opposed to the desktop environment? Just guessing here, but have you installed the UNR (Ubuntu Netbook Remix) and then switched to the regular looking Ubuntu? What's the deal with the menu and task bar? Can you see the top and bottom panels?

You are correct I installed netbook, did not like the look so switched it to classic look. I ended up just reinstalling UNR and switched it back to classic look. I am not sure if it will do it again.

---

### Post by mikewhatever on 2009-08-05
I am afraid it will happen again after a reboot or logout/login. Check out the link below for explanations and a fix.
[http://www.ubuntumini.com/2009/04/desktop-swticher-is-kind-of-broken.html](http://www.ubuntumini.com/2009/04/desktop-swticher-is-kind-of-broken.html)

---

### Post by Greasy_Larry on 2009-08-05
> **mikewhatever said:**
> I am afraid it will happen again after a reboot or logout/login. Check out the link below for explanations and a fix.
[http://www.ubuntumini.com/2009/04/desktop-swticher-is-kind-of-broken.html](http://www.ubuntumini.com/2009/04/desktop-swticher-is-kind-of-broken.html)

Thank you for your response, it has not acted up yet, but if it does, I will do that. If it aint broke dont fix it. I forgot to mention I put a different background picture on the desktop. One that was bigger than the screen. I did not do that again, because before reading your post I assumed that was all it could be. I will respond again if it does happen again. If I do not respond back any further readers at this point can assume the problem was in the larger background pic. My monitor is a 1024x600 and the picture I used was a 1200x800 I think.

---

### Post by ugm6hr on 2009-08-05
It is worthwhile just removing the netbook-remix packages if you are not going to use them, since they always launch at boot, and it is tempting to use the switcher.

From memory - they are **netbook-launcher** and **ubuntu-netbook-remix**.

```
sudo apt-get remove **netbook-launcher** and **ubuntu-netbook-remix**
```

---

