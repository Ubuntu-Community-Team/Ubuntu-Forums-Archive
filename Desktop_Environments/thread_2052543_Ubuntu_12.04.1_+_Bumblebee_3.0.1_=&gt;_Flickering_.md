---
title: "Ubuntu 12.04.1 + Bumblebee 3.0.1 =&gt; Flickering screen"
date: 2012-09-03
forum: Desktop Environments
---

### Post by titusjaka on 2012-09-03
Hello, forum users!
I have a laptop Samsung 300v5a-s19 with NVIDIA GeForce GT 520MX.
I have just installed Ubuntu 12.04.1 and then Bumblebee 3.0.1.
Now it works well without any lags, but there is one problem: when I try to change the screen brightness (by Fn buttons or in the System Settings (Brightness and lock)), display starts flickering. That is, I can not dim the screen.
Does anyone know what the problem is and how to solve it?
Thanks for your aid.

---

### Post by titusjaka on 2012-09-03
I found one more problem: screen starts to twinkle if charger is not plugged in to laptop. It doesn't start immediately, but several minutes later.
What can it be?

---

### Post by dadix on 2012-09-04
i have the same problem on my Samsung but i don't have Nvidia or Bumblebee instaled .

---

### Post by titusjaka on 2012-09-06
Hi, every Samsung laptop users!
I think, I found the solve of this issue.
To stop flickering of your display you should install samsung-tools package:
```

sudo -s
add-apt-repository ppa:voria/ppa && apt-get update && apt-get install samsung-backlight samsung-laptop samsung-tools
reboot

```
After this you will enable to dim your screen back-light =)
Hurrah!

More info:
[https://launchpad.net/~voria/+archive/ppa](https://launchpad.net/~voria/+archive/ppa)
[http://www.voria.org/forum/viewforum.php?f=3&sid=08bf9c3c9a1c81c52fe98dad6f7bccb1](http://www.voria.org/forum/viewforum.php?f=3&sid=08bf9c3c9a1c81c52fe98dad6f7bccb1)

---

### Post by mockturtlesoup on 2012-09-15
Dear users,.

i have a samsung 300e5a, too and had the same problems. I solved it as suggested in the previous post. at least the fn+back light works.

Kind Regards
Tobias

---

### Post by Alark on 2012-09-26
Great work @titusjaka
I have a samsung laptop and the solution given by u works like charmingly.
Thanks for sharing this.
Happy Ubuntu To all .. :)

---

### Post by titusjaka on 2012-09-30
> **Alark said:**
> Great work @titusjaka
I have a samsung laptop and the solution given by u works like charmingly.
Thanks for sharing this.
Happy Ubuntu To all .. :)
Nice to read it =)

---

