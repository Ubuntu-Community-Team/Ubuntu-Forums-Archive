---
title: "Copy paste (mouse select text buffer / clipboard ) broken?"
date: 2017-12-11
forum: Desktop Environments
---

### Post by sirkubax on 2017-12-11
Hello

I do experience random issues while using mouse "select text buffer"  (select text, middle mouse click)
It started few (1-4) months ago - I bet after some system upgrade (so it may be dated longer in the past).

The buffer works randomly - sometimes it copy the selected text for hours, and then, no matter how I do select the text (even trying to paste it back to the same window) - it does paste the "previous" content of a buffer. After a while - it works again.

What has been changed recently?

---

### Post by ajgreeny on 2017-12-11
Just a thought; have you checked your mouse hardware?

I sometimes have the same problem and have to middle click very hard a few times to get the paste working again. 
 
I also find it works better if I roll the scroll-wheel very hard and click while using scroll, but with the computer turned off; I suspect some dust has got into the workings of my mouse which is now pretty old , but otherwise works fine.

---

### Post by sirkubax on 2017-12-14
Well

It started after I reinstall/update 3 different computers with different hardware (Lenovo x230, t430, Shuttle DS81)
Common factor is Lenovo keyboard and Lenovo USB keyboard - I use the trackpoint and it's mouse button.

This was not happening before the updates - so I do assume it is highly related to some bug in system configuration that did come with the update.

---

### Post by again? on 2017-12-14
Install xsel.
```
sudo apt install xsel
```
When the middle click paste fails to work, type xsel in terminal to see if there is anything in your primary selection buffer.

---

