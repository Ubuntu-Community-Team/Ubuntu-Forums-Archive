---
title: "[KDE fonts] Special characters"
date: 2005-10-08
forum: Desktop Environments
---

### Post by Fipaj on 2005-10-08
Hi!

(I know that this isn't first that thread, but I need help).

I'm working on GNOME Ubuntu, but now I'm going to install some KDE applications.

I installed KControl and Polish localization of KDE :)

Everything going OK, but look at this screenshot:

[[img=http://img58.imageshack.us/img58/5589/zrzutekranu6kz.th.png]](http://img58.imageshack.us/my.php?image=zrzutekranu6kz.png)

Do you see that there's no polish special characters? I don't know how to make it OK :/

Can you help me? :)

Best Regards,
Fipaj

---

### Post by mlomker on 2005-10-08
You installed Polish under Country/Region & Language?  I'm assuming that the rest of your system already has the proper locale installed...you picked Polish when you initially installed your machine?  Run **sudo dpkg-reconfigure locales** from a command-line if you're not sure.

After that you'd have to go into Appearance & Themes, Fonts and be sure to select a font that offers all of the characters that you need.

---

### Post by Fipaj on 2005-10-08
I have installed pl_PL.UTF-8 UTF-8. And GNOME is well-working with polish langauge...

I have installed kde-i18n-pl package, so menus and apps are in Polish. But special characters not :/

> You installed Polish under Country/Region & Language? Yes!

All works fine. But there's no polish special chars :/

---

### Post by mlomker on 2005-10-08
> All works fine. But there's no polish special chars :/

You'll have to find some Truetype fonts with the Polish characters and then install them.  I'm not sure where you'd get those.  If you have some font files from Windows then there are ways to import them.

---

### Post by Fipaj on 2005-10-08
Hey!

Thanks for your help. I find one font with polish chars, FreeSans, and now i'm looking for next in kde-look.org.

Best regards,
Fipaj

---

