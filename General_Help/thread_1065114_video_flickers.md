---
title: "video flickers"
date: 2009-02-09
forum: General Help
---

### Post by SonnHalter on 2009-02-09
someone told me to edit options for something to make it work. but i don't remember how to get to them.

---

### Post by kaurman on 2009-02-09
Do you mean [this bug?]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/214787")

In that case, check out the last post. 

If your symptoms are different then maybe you could be a bit more specific. What kind of hardware are you using, when does the bug occur...

K

---

### Post by SonnHalter on 2009-02-09
no, i didn't have to gedit. it was something like editing options and I had to choose somehting along the lines of "do not use xvideo blah"

---

### Post by SonnHalter on 2009-02-09
bump

---

### Post by Yashiro on 2009-02-09
What flickers? 
Which Ubuntu? 
What video card? 
Which driver?
What are you trying to do?

In short, give more info and get better help.

---

### Post by SonnHalter on 2009-02-09
how do i get to edit the totem options

---

### Post by sedawk on 2009-02-09
I have a onboard-ATI graphics chipset and to turn of that flickering
I have to replace compiz with another window manager.
What I do is this:
```

pkill compiz;sleep 2;nohup metacity &

```

Do you only get flickering with totem but not with
mplayer or VLC?

---

