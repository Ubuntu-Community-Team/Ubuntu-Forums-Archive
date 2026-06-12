---
title: "Firefox Problems"
date: 2009-04-25
forum: General Help
---

### Post by SCChuck1354 on 2009-04-25
Hey guys this is my first post as well as my first questions. I'm kinda new to Ubuntu, even though I've had it for about a year. Its done all I've wanted it to do for me in the past year, but recently I've had a little problem. Whenever I open up Firefox, it is open for a few seconds and then just closes. I have tried reinstalling Firefox. But I can't use any online virus detection services because Firefox is my only web browesr that is able to handle such a thing. I'm currently using Konquerer to send this, but it will not do any of the things that I need my computer for. **Help me**!!! 

                                              Chuck

---

### Post by jbrown96 on 2009-04-25
Try launching it from the terminal, then post all of the output it generates.

---

### Post by SCChuck1354 on 2009-04-25
Ok im not the best with a computer what do you mean?

---

### Post by jbrown96 on 2009-04-25
Go to Applications--->Accessories--->Terminal then launch firefox with ```
firefox
``` Copy and paste the output

---

### Post by SCChuck1354 on 2009-04-25
GCJ PLUGIN: thread 0x805e908: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x805e908: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x805e908: NP_GetValue
GCJ PLUGIN: thread 0x805e908: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x805e908: NP_GetValue return
GCJ PLUGIN: thread 0x805e908: NP_GetValue
GCJ PLUGIN: thread 0x805e908: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x805e908: NP_GetValue return
GCJ PLUGIN: thread 0x805e908: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x805e908: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x805e908: NP_GetValue
GCJ PLUGIN: thread 0x805e908: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x805e908: NP_GetValue return
GCJ PLUGIN: thread 0x805e908: NP_GetValue
GCJ PLUGIN: thread 0x805e908: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x805e908: NP_GetValue return
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault

---

### Post by SCChuck1354 on 2009-04-25
So what does this mean and how should i fix it? anyone got an answer :confused:







                                        Chuck  :guitar:

---

### Post by SCChuck1354 on 2009-04-25
so does anyone know????? -.-

---

### Post by SCChuck1354 on 2009-04-26
can i get some help here????????????????????

---

### Post by lvleph on 2009-04-27
Try opening terminal and type 
```

firefox -safe-mode

```
Then go to tool >> addons >> plugins and disable the icedtea plugin.
Close firefox and try to start it like normal. You want be able to use java if this works.

---

