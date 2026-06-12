---
title: "How do you fix screen resolution (after install)?"
date: 2012-04-29
forum: Desktop Environments
---

### Post by Elzenbr8 on 2012-04-29
So, how do you fix screen resolution after installing ubuntu?
Preferable resolution: 1920x1080
Preferable driver: ati radeon (open source)

---

### Post by niteling on 2012-04-29
which version of ubuntu? if you're using 12.04 the just go to system settings on the unity bar and from there go to display.

---

### Post by Elzenbr8 on 2012-04-29
> **niteling said:**
> which version of ubuntu? if you're using 12.04 the just go to system settings on the unity bar and from there go to display.
Yup, it's 12.04. But that way won't solve it. I wonder how...
I've tried xrandr too, but still got the same.

---

### Post by niteling on 2012-04-29
so xrandr is like the nvidia drivers but for ati? And you stil can't configure the resolution. hmm

---

### Post by Elzenbr8 on 2012-04-29
> **niteling said:**
> so xrandr is like the nvidia drivers but for ati? And you stil can't configure the resolution. hmm

It's not like I can't configure it. I can set it lower.
My apologies for not telling the whole story before. So, here you go:
> 
On my 12.04, by default screen resolution detected correctly, 1920x1280 (16:9). But I wonder why the top bar and the sidebar (unity) shown half. It looks wider.
To fix that, I need to set it lower than my preferable resolution, to 1680x1050 (16:10).
But, GDM won't change. It's still wider, and I can't see the bar and its menus.
By the way, lowering screen resolution to 16:10 is not that good today, I think. For example, you can't get full screen of your 16:9 movies, unless you override them through movie player.
Well, any suggestions to solve this matter...

Or might be (if not possible), how to change GDM resolution, so that it sync with desktop environment?

---

### Post by niteling on 2012-04-29
OK sorry, I can't help you here, I'm pretty new to ubuntu. I've got a to learn. whats GDM?

---

### Post by Elzenbr8 on 2012-04-29
That's OK, thanks for your consideration..

---

### Post by niteling on 2012-04-29
do you know anything about samba sharing?

---

### Post by Elzenbr8 on 2012-04-29
> **niteling said:**
> do you know anything about samba sharing?
A few things

---

### Post by Elzenbr8 on 2012-05-02
**Solved**, by:
Changing to the lower resolution (1680x1050).
Override movie aspect to 16:10.
Synchronize login screen and desktop using the same resolution (1680x1050).

Works with gdm and lightdm.
And with open source graphic driver installed.

***No wider looking anymore***

Using 1920x1080 is also working, but all the text displayed blurries.

---

