---
title: "Screen flashing while playing"
date: 2012-03-12
forum: Gaming &amp; Leisure
---

### Post by clm22 on 2012-03-12
I'v used Ubuntu for a while now and just reinstalled it after windows decided to play up. I installed the 32 bit Ubuntu 11.10 and installed wine and the games I play (counter strike for one) and launched it and found the screen to flash every second or so. I thought it was with wine and installed minecraft but when i played it in fullscreen the same was happening (windowed was fine but laggy) so I'm now guessing it's my driver. in previous versions it selected proprietary drivers and installed them and the games ran smoothly but in 11.10 no additional drivers were suggested. Any idea what is causing this and how to fix it? If it helps I use a nvidia graphics card.

Thanks :D

---

### Post by Perfect Storm on 2012-03-13
Please post the output of this command:

```
lspci |grep VGA
```

---

### Post by clm22 on 2012-03-13
> **Artificial Intelligence said:**
> Please post the output of this command:

```
lspci |grep VGA
```

Ok sorry I'm a bit late :)

02:00.0 VGA compatible controller: nVidia Corporation Device 0ca5 (rev a2)

---

### Post by clm22 on 2012-03-13
Nvm I found a solution :) I just followed this tutorial and installed the latest drivers and now everything works out fine :)  
Thanks for the help XD

([http://www.youtube.com/watch?v=0iyw4-KcPMg](http://www.youtube.com/watch?v=0iyw4-KcPMg)) for anyone else that has this problem :D

---

