---
title: "GTK app fonts too big in KDE (Kubuntu Gutsy)"
date: 2008-01-07
forum: Desktop Environments
---

### Post by Schuenemann on 2008-01-07
Hi,

I just installed Kubuntu Gutsy and I noticed something weird that didn't happen in Feisty.
Firefox and Thunderbird (the only applications I noticed, so I suppose GTK is my problem) fonts are too big and don't fit my screen.

Below are 2 screenshots that show the problem.
Firefox: [http://img527.imageshack.us/img527/2619/fxprobsi3.jpg](http://img527.imageshack.us/img527/2619/fxprobsi3.jpg) (look below google bar)
Thunderbird: [http://img528.imageshack.us/img528/3329/tbprobnx0.jpg](http://img528.imageshack.us/img528/3329/tbprobnx0.jpg) (search bar)

In systemsettings I have "use KDE style" checked. I tried reducing the size to 8 and that solved the problem, but then the font is too small.

I want those application to run as they used to in Feisty.

Thanks.

---

### Post by luisromangz on 2008-01-08
Well I solved this forcing the DPI value in KControl Font settings panel to 96ppp. You should try this too.

---

### Post by Schuenemann on 2008-01-08
How do I set it to 96?
I only have 3 options: disabled, % DPI and 120 DPI, which is bigger than what I have currently.

Thanks

---

### Post by Schuenemann on 2008-01-11
Bumping and hoping someone has a suggestion.

---

### Post by rpkehoe on 2008-01-11
Thanks, this did the trick for me.  I had the opposite problem, everything was tiny and I couldn't read it.

---

### Post by TeaSwigger on 2008-01-11
> **Schuenemann said:**
> How do I set it to 96?
I only have 3 options: disabled, % DPI and 120 DPI, which is bigger than what I have currently.

Thanks

In system settings, appearances, fonts, you should see a selection to "force fonts DPI" - you should have 96 dpi as an option. Setting that should fix things... luck.

---

### Post by Schuenemann on 2008-01-16
I don't. I only see those values I said: disabled, % DPI and 120 DPI.

---

### Post by samwyse on 2008-01-16
> **Schuenemann said:**
> I don't. I only see those values I said: disabled, % DPI and 120 DPI.

I suspect there's a translation bug that has changed the "96" to "%", that is if you're using something else than English? Just apply the setting and log out and then back.

---

### Post by Schuenemann on 2008-01-16
> **samwyse said:**
> I suspect there's a translation bug that has changed the "96" to "%", that is if you're using something else than English? Just apply the setting and log out and then back.

Yes, I'm using pt_BR.
IIRC, I have tried that setting too, but I'll double check when I get home.
Thanks

---

### Post by Schuenemann on 2008-01-16
I did that, restarted X, but nothing changed.

---

### Post by Schuenemann on 2008-01-20
Bumping again. I hope this doesn't break any rule.

---

