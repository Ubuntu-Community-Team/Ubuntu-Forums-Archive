---
title: "more resolution problems"
date: 2008-12-30
forum: General Help
---

### Post by 2handband on 2008-12-30
I did not install any updates. I made no system configuration changes whatsoever. I restarted my laptop which has never had resolution issues before and discovered that everything was way too big. I got into my res settings and the best resolution I can get is 800x600.

What is going on here? This is the third time something has abruptly went haywire on my Ubuntu install when I made no changes. Worse, since I've had this same problem on another computer I have some doubts about my ability to resolve this one. I need this laptop for day-to-day productivity. Can somebody please tell me what gives here?

---

### Post by 2handband on 2008-12-30
Okay, now I'm REALLY confused. I restarted and it's back to normal. What is going on here?

---

### Post by hal8000 on 2008-12-30
You need to at least post your laptop make/model and graphics chipset.

It sounds as though the graphics driver has not loaded and dropped back to vga resolution. Sometimes a reboot will cure this with no other work necessary.


Can you also post output of:
sudo lspci

(You can snip the lines that dont contain your Graphics chipset)

---

### Post by gettinoriginal on 2008-12-30
Sounds like your xorg did a "burp" while booting the first time.  As long as it is back to normal, you know that nothing is "broken"  :P

---

