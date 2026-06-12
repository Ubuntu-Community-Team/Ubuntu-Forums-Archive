---
title: "xfce 4.2"
date: 2005-04-20
forum: Desktop Environments
---

### Post by GOwin on 2005-04-20
I tried to change my screen resolution from xfce, now the screen is unreadable everytime i log into xfce. Logging into gnome doesn't give me any problem.

how can i fix this?

---

### Post by ZeroVerteX on 2005-04-20
Try running "xfce-setting-show" from Gnome and see if you can reset the res from there.

---

### Post by GOwin on 2005-04-20
Nope, it doesn't work. I only get the same screen like I had in xfce.

(why do this happen? I mean, I know my laptop can support 800x600, i just wanted to see how it looks like at that screen resolution ... :( )

---

### Post by GOwin on 2005-04-26
I still have not managed to resolve this.

I already completely removed XFCE, and then re-installed it but I still see a gibberish screen whenever I log to it. Gnome still works fine.

Could anyone please help me?

---

### Post by GOwin on 2005-04-27
bump

---

### Post by GOwin on 2005-04-27
I got the answer from [XFCE forums](http://www.os-cillation.de/cgi-bin/yabb/YaBB.cgi?board=deb-help;action=display;num=1109910123): remove the configuration files.

```
rm -rf ~/.xfce4/ ~/.config/xfce4* ~/.cache/
```

That did it.

---

