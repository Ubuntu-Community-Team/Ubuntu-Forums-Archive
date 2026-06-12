---
title: "2 problems please help"
date: 2008-03-31
forum: Desktop Effects &amp; Customization
---

### Post by SuperXero on 2008-03-31
im running ubuntu 7.10 on an acer aspire 5670 (ati vid card, intel processor) and I just installed the video driver. I was able to change my resolution, but now when i try to enable the desktop effects I got the error "the composite extension is not available". i used the command "$ sudo apt-get install xserver-xgl" and now once i try to enable the desktop effects it now says "desktop effects could not be enabled" 

one other problem i have is now the i am able to change the resolution on my laptop, it seems as though the driver didnt fully install, because when i try to scroll down on the forums it lags.

---

### Post by aroch1 on 2008-04-01
I don't know about the second problem, but if you open up a terminal, execute

```
compiz --replace
```

and paste the output here, I'd be able to get a better idea of why you can't enable desktop effects.

---

