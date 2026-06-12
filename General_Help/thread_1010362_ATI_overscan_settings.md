---
title: "ATI overscan settings"
date: 2008-12-13
forum: General Help
---

### Post by fragglerock585 on 2008-12-13
Hello everyone, I just registered, but I'm not new here.  I've been lurking and getting my support by searching/reading.

I have an issue that I can't figure out how to solve though.  I have a 780G based motherboard (ATI 3200 Graphics) which I have hooked up to a Sony SXRD tv, which means that I have to deal with some slight overscan.  I've figured out how to correct it though four aticonfig commands, changing the xy position and size through the terminal.  However, this only works for the current desktop session.  

Is there a way I can set these values permanently?

Thanks!

---

### Post by jbrown96 on 2008-12-13
Try this instead. ```
sudo aticonfig --set-pcs-val=MCIL,DigitalHDTVDefaultUnderscan,0
```

---

### Post by fragglerock585 on 2008-12-14
> **jbrown96 said:**
> Try this instead. ```
sudo aticonfig --set-pcs-val=MCIL,DigitalHDTVDefaultUnderscan,0
```



I've tried that, but unfortunately it leaves off the outside of my screen, including all of the bars around the edges.  This is a result of a built in and undefeatable (its mechanical, NOT electronic) overscan on this projection tv.  As a result, I need to underscan by a few percent on each edge.  

Thanks for the help!

---

