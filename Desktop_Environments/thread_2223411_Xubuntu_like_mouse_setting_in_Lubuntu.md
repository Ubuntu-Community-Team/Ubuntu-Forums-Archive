---
title: "Xubuntu like mouse setting in Lubuntu"
date: 2014-05-10
forum: Desktop Environments
---

### Post by c2tarun on 2014-05-10
[HR][/HR]Hi friends,

This might look like a weird question but I really want this. I was a Xubuntu 12.04 user till 14.04 came out. I did a fresh install of Xubuntu 14.04 and found it heavy, slow, heating my laptop and slightly buggy. So I downloaded and installed Lubuntu 14.04. I am loving it, its very stable and fast.
Now I use a USB mouse as well as touchpad on my laptop. I use USB mouse with left hand and Touchpad with right hand :(. In Xubuntu if we go to "Mouse and Touchpad" Settings we see there two tabs, one to control your touchpad and other to control you mouse. So I was easily able to set USB mouse as left hand and touchpad as right hand. But in Lubuntu I have only one tab which is changing both touchpad and mouse to left hand. Is there any way of bringing Xubuntu mouse setting to Lubuntu?

---

### Post by bapoumba on 2014-05-11
Probably not a complete answer, but may be setup the mouse and touchpad for left handed and then work on touchpad to get it right handed.

Ideas from here : [http://ubuntuforums.org/showthread.php?t=1746468](http://ubuntuforums.org/showthread.php?t=1746468)

11 is my touchpad id and is currently set up for right handed :
```
xinput get-button-map 11
1 2 3 4 5 6 7 8 9 10 11 12
```

I have not fully tested, changing the mouse/touchpad menu works for me, but freezes my session that becomes completely unusable, I have to restrat LightDM from a virtual terminal. This is an unrelated issue I think as I had the same effect tweaking the keyboard the other day, and I now think it comes from me exiting ibus to have text input into Chromium working (there is a bug about it).

---

