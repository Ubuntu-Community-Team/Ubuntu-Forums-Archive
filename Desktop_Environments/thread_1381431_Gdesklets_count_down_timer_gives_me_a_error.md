---
title: "Gdesklets count down timer gives me a error"
date: 2010-01-14
forum: Desktop Environments
---

### Post by psyboy55 on 2010-01-14
when i try to run countdown2 applet it tell me
```
 No Control could be found for interface ITime:7qktelp6tw29ve5p8q3lxn6bs-2
/usr/share/gdesklets/Displays/countdown/countdown2.display
```

---

### Post by hikerdude07 on 2010-03-31
Me too. I'm searching for a work around. I'll post if figure it out

---

### Post by soowjo on 2011-09-16
1. Run either Clock or Calendar that are installed as default packages.
2. Right click on the desklet that you just ran.
3. Left click on "View Source" in the drop-down menu.
4. Find something that reads **interface="ITime:1g234wdpgke5e879asdfgr24f"**
5. Copy and paste what comes between the colon and the ending quotation mark (e.g. **1g234wdpgke5e879asdfgr24f**)
6. Run Coundown now.
7. Right click on Countdown desklet
8. Left click on "View Source" in the drop-down menu.
9. Find something that reads **interface="ITime:235dk41sodi5soepqlcjrusoq-2"**
10. Paste what you copied (e.g. **1g234wdpgke5e879asdfgr24f**) over what is between the colon and the ending quotation mark (e.g. **235dk41sodi5soepqlcjrusoq-2)**

---

