---
title: "Unity on 12.04"
date: 2012-10-11
forum: Desktop Environments
---

### Post by Azyx on 2012-10-11
Hi.
I have a little problem. When I sometimes click applications-icon on the launcher, the icon, move a little bit on the diagonal, and do not 'puls', and the application does not start. Why does that happend?
The launcher get some signal because it move, but it does not start?

/Cheers

---

### Post by Frogs Hair on 2012-10-11
Could you please list what application/s are not opening.> do not "puls" 
I 'm not sure what you mean by this .

---

### Post by Azyx on 2012-10-11
> **Frogs Hair said:**
> Could you please list what application/s are not opening. 
I 'm not sure what you mean by this .

The colour, transparency or glowing change on  when you click on it, to tell you that you have clicked on the icon. The launcher icon do normaly not move sideways, then you click on it.

All application and even folders. And if i click onther time, it works, if the icon don't move sideways.....

---

### Post by Azyx on 2013-03-31
bump

Can't find "edit" in my head post not are not able to mark the thread as solved...

---

### Post by vanadium on 2013-03-31
Maybe you click to "long". When the click is longer, it is interpreted as the start of a drag operation. You may want to adjust the "Drag and drop" threshold setting.

---

### Post by Frogs Hair on 2013-03-31
The launcher behavior settings are pretty limited without the ccsm or other software . You can try removing the applications from the launcher and re adding them, but I don't know if unity is the problem for sure . When the application fails to open start it from the terminal by typing the name and watch for errors. As a last resort use the following command .   ```
 unity --reset
```

---

### Post by Azyx on 2013-03-31
Yes it could be... But if you click and hold, the symbol move up or down. I think it can be little different kick-signas depending on which mouse you have... It could also have being 'fixed' do I only get it on a live-session now.

/Cheers

The problem was the launcher, not application, but it seems to be fixed now.

---

### Post by Frogs Hair on 2013-03-31
I was able to duplicate the diagonal shift and it was caused by unintentional dragging.

---

### Post by Azyx on 2013-09-26
> **Frogs Hair said:**
> I was able to duplicate the diagonal shift and it was caused by unintentional dragging.

Thanx! Maybe I was little shake-handed ;)

---

