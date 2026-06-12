---
title: "grecord broke"
date: 2005-04-21
forum: Desktop Environments
---

### Post by kiddo on 2005-04-21
Hi, I'm sorry if this has already been posted, but I haven't found anything yet. Besides, this is a bit weird. I haven't done anything special except removing Openoffice2 and reinstalling Openoffice1.1.

This is on a stable hoary laptop. Tonight, as I was about to start recording my lesson as usual... the gnome sound recorder just didn't want to start. A nice error dialog saying:
"Registry is not present or it is corrupted, please update it by running gst-register."
Okay, I RTFineM of gst-register, but I didn't quite know what to do next anyhow. So I tried apt-get removing gnome-media, and installing it back, but I noticed some warnings during the removal. Didn't note them, sorry. But here, when I installed it back, I got some more menacing warnings, such as:
"ldconfig: /usr/lib/libclanCore.so.2 is not an ELF file - it has the wrong magic bytes at the start"

I am no programmer, so I don't know the term magic bytes. I wouldn't know how to fix it anyhow.

---

### Post by kiddo on 2005-04-23
I have found my solution myself, looks like no one was awake at that time, so I'm adopting my own unanswered thread.

I just had to run 
**gst-register-0.8**

Not
**gst-register**


I hope this thread may help some people in the future ;)

---

