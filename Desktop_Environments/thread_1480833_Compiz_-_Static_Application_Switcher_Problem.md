---
title: "Compiz - Static Application Switcher Problem"
date: 2010-05-12
forum: Desktop Environments
---

### Post by LeboyX on 2010-05-12
While I'm a huge fan of Compiz, the latest version that came with Ubuntu 10.4 has an unwanted feature I cannot disable. 

When cycling through my windows with "ALT + TAB", each window I cycle through is immediately brought ("faded") to my desktop, whether I have selected it or not. While I'm sure this is nice for some, it's slow and distracts from what I'm actually trying to do. 

Is there any way to disable this auto-display feature?

---

### Post by markbl on 2010-05-12
I actually like this feature but can understand not everybody may. You would think the ccsm static app switcher "Highlight Mode = Bring Selected To Front" default option changed to "None" would do what you want but it does not seem to change anything?

---

### Post by LeboyX on 2010-05-12
Indeed...selecting "none" for that field doesn't seem to affect switching at all. Am I missing its affect, or is this a bug?

---

### Post by mlissner on 2010-07-06
Yeah, this appears to be a rather annoying bug. I've tried changing it in gconf-editor and in ccsm. Both efforts failed for me.

---

### Post by Boludinux on 2010-08-26
I have exacly the same problem, bump

---

### Post by Cavsfan on 2010-08-26
I use "Shift Switcher" (CCSM - Window Management). ALT+TAB shows the open objects in a ring.
It works well and I am happy with it. ALT+TAB goes to Next Window, but I did have to enter a 
command for Previous Window (Shift+ALT+TAB) to go the other way.

I like it.

---

### Post by Boludinux on 2010-08-26
> **Cavsfan said:**
> I use "Shift Switcher" (CCSM - Window Management). ALT+TAB shows the open objects in a ring.
It works well and I am happy with it. ALT+TAB goes to Next Window, but I did have to enter a 
command for Previous Window (Shift+ALT+TAB) to go the other way.

I like it.

When I discovered this bug I started using it too but its not the same, I feel it a lot more unconfortable when a try to find an application and I have 6+ windows opened.  

So thats not a solution sorry.

---

### Post by Cavsfan on 2010-08-26
> **Boludinux said:**
> When I discovered this bug I started using it too but its not the same, I feel it a lot more unconfortable when a try to find an application and I have 6+ windows opened.  

So thats not a solution sorry.

Maybe that's not _your_ solution. We haven't heard the OP's opinion.
There are a lot of settings in Compiz which can lead to confusion.

---

### Post by sacapeao on 2011-04-24
@Mint 10 Julia:
~ $ compiz --version
compiz 0.8.6
highlight mode: None brings selected windows to front

---

### Post by sacapeao on 2011-04-24
found a workaround
select highlight mode: None + set Opacity to 100%

---

