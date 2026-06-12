---
title: "howto set webkit as default in konqueror?"
date: 2009-02-03
forum: Desktop Environments
---

### Post by yangcheng on 2009-02-03
Hi:
I have install webkitkde and konqueror in kde4.2.

It is possible to switch to webkit from menu-view-view-mode. and webkit engine works perfect for gmail

I think it should be trial to set webkit as default, however, I could not find the option everywhere I tried.

Any suggestions? thanks

---

### Post by sebaxtian on 2009-02-04
If you want to set the WebKit part as default, run:

keditfiletype text/html

and move "WebKit (webkitpart)" in the "Embedding" tab to the top.

---

### Post by pritamps on 2009-02-04
GMail still works only in HTML mode, though, even after this :(

---

### Post by yangcheng on 2009-02-04
> **sebaxtian said:**
> If you want to set the WebKit part as default, run:

keditfiletype text/html

and move "WebKit (webkitpart)" in the "Embedding" tab to the top.

great!
It works

---

### Post by mojorising on 2010-02-08
pritamps, try going into the Browser Identification section of Konqueror's configuration (Settings > Configure Konqueror > Browser Identification (in the left pane of that configuration window). Click New under Site Specific Identification. There, create an item for google.com. Set the identification string as Google Chrome. 

That's how I have mine set and it works no problem. Hopefully it does the trick for you as well. 

Mike

---

### Post by nortexoid on 2010-10-20
> **sebaxtian said:**
> If you want to set the WebKit part as default, run:

keditfiletype text/html

and move "WebKit (webkitpart)" in the "Embedding" tab to the top.

Awesome.

---

### Post by nortexoid on 2010-10-20
> **mojorising said:**
> pritamps, try going into the Browser Identification section of Konqueror's configuration (Settings > Configure Konqueror > Browser Identification (in the left pane of that configuration window). Click New under Site Specific Identification. There, create an item for google.com. Set the identification string as Google Chrome. 

That's how I have mine set and it works no problem. Hopefully it does the trick for you as well. 

Mike

Didn't work for me, unfortunately.

---

