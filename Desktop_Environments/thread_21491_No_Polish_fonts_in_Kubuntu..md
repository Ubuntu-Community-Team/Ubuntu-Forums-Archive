---
title: "No Polish fonts in Kubuntu."
date: 2005-03-22
forum: Desktop Environments
---

### Post by CitricAcid on 2005-03-22
I was trying to set my KDE to Polish. But everything (almost) is in English. And also there are no Polish fonts. How to make my locale work?

I've installed my locales (-pl)

I use Hoary.

---

### Post by aramazan on 2005-03-23
[QUOTE=CitricAcid]
I've installed my locales (-pl)
[/QUOTE]

Assuming you meant that you installed the "locales" package and set it up for Polish, "apt-cache search polish" lists a lot of additional Polish i18n & l10n related packages. I would have installed at least, kde-i18n-pl (possibly your current problem) and language-env (maybe your next problem) :) I guess there might be several more packages you would want to install from apt-cache listing.

---

### Post by CitricAcid on 2005-03-24
Thanks. I'll try when I get back home.

---

### Post by scarecrow on 2005-03-24
[QUOTE=CitricAcid]Thanks. I'll try when I get back home.[/QUOTE]
 After installing locales you should try
dpkg-reconfigure locales
and pick up polish (plain or UTF8).
and then you will be prompted for the default system language, pick some polish or en_US.UTF8 and you are set.
For the right font configuration, it depends on the xserver you use (xorg 6.8.2 strongly recommended).

---

### Post by CitricAcid on 2005-03-31
Thanks aramazan. Now it's (almost) all in Polish. :)

Thanks scarecrow. I did what you have sugested. But I haven't got Polish diacritical signs :(
I have updated my hoary and use xorg 6.8.2. But some signs are 'squared' :(
How to fix it?

---

### Post by CitricAcid on 2005-04-01
Can anybody help??

---

### Post by Cmykus on 2005-04-01
[QUOTE=CitricAcid]Can anybody help??[/QUOTE]

I have this same error...



Mam to samo i nie wiem jak to skonfigurowac zeby bylo ok.

---

### Post by aramazan on 2005-04-02
[QUOTE=CitricAcid]Can anybody help??[/QUOTE]
I had a similar error once. It was something to do with mismatched use of iso-8859-9 and utf-8. That is, translations was in utf-8 but KDE was displaying them in iso-8859-9 (or the other way, I don't remember clearly). I guess the best people to help you is KDE Polish translation team. Also, scarecrow's suggestion regarding iso vs. utf-8 setup of language environment might help. I would suggest finding other Polish users of KDE 3.4 (Polish LUG?) and asking them if they experience the same problem. Their solution should equally apply to you as well.

Best regards,

---

### Post by aramazan on 2005-04-02
[QUOTE=Cmykus]I have this same error...[/QUOTE]
Now I too have this same error in OO.o/Kubuntu-RC. Posted it at [http://lists.ubuntu.com/archives/kubuntu-users/2005-April/000186.html](http://lists.ubuntu.com/archives/kubuntu-users/2005-April/000186.html)

---

### Post by Cmykus on 2005-04-02
Now , polish fonts work for me :)


I only change font in control center to verdana :) 

Polish sings work ok :)

---

