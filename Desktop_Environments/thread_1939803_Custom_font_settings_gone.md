---
title: "Custom font settings gone"
date: 2012-03-12
forum: Desktop Environments
---

### Post by Erik1984 on 2012-03-12
I'm more looking for an explanation than an actual solution but here's the problem: When I booted my Kubuntu 11.10 this morning the fonts were all small again. I don't like Kubuntu's fonts OOTB so I changed some font settings. Up till this morning it remembered my font settings correctly each time. Somehow the font setting got spontaneously reverted to the defaults. How can that happen? Other KDE setting don't seem to be affected. :-k

---

### Post by Erik1984 on 2012-09-25
Recurrence bump :P Exact same thing happened again in Kubuntu 12.04.1. It's not hard to restore but annoying nonetheless.

---

### Post by PaulW2U on 2012-09-25
Just so you know someone has read your posts, I can honestly say it hasn't happened to me. :)

I've been running Kubuntu since 11.04 and have used every version since then including alpha and beta versions. Presumably you haven't installed any program that might change fonts? Strange.

---

### Post by Erik1984 on 2012-09-25
> **PaulW2U said:**
> Just so you know someone has read your posts, I can honestly say it hasn't happened to me. :)

I've been running Kubuntu since 11.04 and have used every version since then including alpha and beta versions. Presumably you haven't installed any program that might change fonts? Strange.

Now that you mention it... (seriously didn't think about this connection yet) I did install GSmartControl (GTK frontend to smartmontools) to check hard drives. Then I shut my computer down and switched it on few hours ago. GSmartControl did have very small text.

---

### Post by kio_http on 2012-09-27
Do note that when you change fonts in system settings it does not affect the fonts of root programs.

I had this problem only once I believe on Kde 4.8 but it has disappeared maybe because I am now on KDE 4.9.1.

---

### Post by Erik1984 on 2012-09-27
> **kio_http said:**
> Do note that when you change fonts in system settings it does not affect the fonts of root programs.

I had this problem only once I believe on Kde 4.8 but it has disappeared maybe because I am now on KDE 4.9.1.

Well, GSmartControl does ask for root password when it starts so that might explain the small text. I haven't toch GSmartControl since I posted my update on the situation here and so far so good: fonts have kept the desired properties.

---

### Post by funicorn on 2012-09-28
try moving your ~/.fonts.conf to ~/.config/fontconfig/fonts.conf

---

