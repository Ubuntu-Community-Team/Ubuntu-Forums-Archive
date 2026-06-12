---
title: "Doubleclick to maximize not working"
date: 2011-05-04
forum: Desktop Environments
---

### Post by avadski on 2011-05-04
Hello,

I've just moved from Mint to Xubuntu. So far I'm very satisfied with this distribution but there's one annoying thing happening to me. 
When I double-clicked the top of the window bar in Windows/Ubuntu/Mint it always got maximized or (when maximized) shrinked to previous size. This is however not the case in Xubuntu. Doubleclicking does nothing :(
I've checked the settings in Menu-> Settings-> Settings Manager-> Window Manager-> Advanced where everything is set properly: Doubleclick action: Maximize Window.
Anyone else having similar problem? Any solutions?

Thanks in advance, Viliam.

---

### Post by spadger on 2011-10-14
I had the same problem in 11.04 and still have the same problem in 11.10.

---

### Post by ankspo71 on 2011-10-14
Hi,
It might be that the default double click time is too fast for your needs (it was way too fast for me). Check to see if the "double click time" is set to a long enough speed at Settings > Settings Manager > Mouse > Behavior > Double Click Time. A value between 570 to 600 is probably good for most people.

Hope this helps.

---

### Post by spadger on 2011-10-15
Set it to 1000 (both infact) but still need to click really fast for it to work

---

### Post by andrei2 on 2011-12-18
See the same. Any solution from anyone?
[edit]

Google says:
[https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/393672/comments/8](https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/393672/comments/8)

This works!

---

### Post by finny388 on 2012-01-04
> **ankspo71 said:**
> Hi,
It might be that the default double click time is too fast for your needs (it was way too fast for me). Check to see if the "double click time" is set to a long enough speed at Settings > Settings Manager > Mouse > Behavior > Double Click Time. A value between 570 to 600 is probably good for most people.

Hope this helps.

It helped! Thanks ankspo! I thought it was broken but that's all it took.:)

---

### Post by Dimitree on 2012-02-10
> **ankspo71 said:**
> Hi,
It might be that the default double click time is too fast for your needs (it was way too fast for me). Check to see if the "double click time" is set to a long enough speed at Settings > Settings Manager > Mouse > Behavior > Double Click Time. A value between 570 to 600 is probably good for most people.

Hope this helps.

Thank you :)

---

### Post by minja on 2012-12-06
Worked for me too! Thanks

---

### Post by zaphod2003 on 2012-12-21
Thanks guys the default setting for double click was set on mine to 250ms.

I reset that to 650 ms and the windows now behave themselves.

---

### Post by rai4shu2 on 2012-12-22
I use 400 ms. That default of 250 is a little nuts.

---

