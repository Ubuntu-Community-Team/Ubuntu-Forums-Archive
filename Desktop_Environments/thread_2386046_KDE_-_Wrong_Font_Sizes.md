---
title: "KDE - Wrong Font Sizes"
date: 2018-02-28
forum: Desktop Environments
---

### Post by holysword on 2018-02-28
Hello there,

I am running KDE, but I am having troubles with having Google Chrome (not Chromium) and Konqueror recognizing the fontsize of the rest of the system. I'm not referring to the font size of the content of the browser, but the interface itself. They seem to get the colours right, but their font size does not match the font size of the rest of the system no matter what I do.

Any ideas of where to start looking for a culprit?

---

### Post by vasa1 on 2018-02-28
Google Chrome will mostly use the font size specified by your **gtk3** theme.

What do you mean by "running KDE"? Which distro, which version?

---

### Post by holysword on 2018-02-28
I am running Ubuntu-16.04 with KDE (plasma-desktop package, not kubuntu-desktop).
I have other DEs installed too, but I'm worried only about KDE now.

I'd guess that the discrepancies between Konqueror and the other KDE applications is that the former relies on KDE4, and the others on KDE5. I am, however, unaware of a way to configure things specifically for KDE4. 

Also, I didn't meddle with GTK at all. KDE's systemsettings, however, does provide appearance configurations for GTK applications, and I've set the font size there too.

---

### Post by holysword on 2018-02-28
> **holysword said:**
> I am running Ubuntu-16.04 with KDE (plasma-desktop package, not kubuntu-desktop).
I have other DEs installed too, but I'm worried only about KDE now.

I'd guess that the discrepancies between Konqueror and the other KDE applications is that the former relies on KDE4, and the others on KDE5. I am, however, unaware of a way to configure things specifically for KDE4. 

Also, I didn't meddle with GTK at all. KDE's systemsettings, however, does provide appearance configurations for GTK applications, and I've set the font size there too.

I just tested KMix (which is also a part of KDE4) and it also misbehaves with respect to font size, but not colours, icons and etc.

---

### Post by holysword on 2018-03-01
I fixed it by installing qt4-qtconfig and then setting the font value in there. There is still some conflict going on somewhere though. Modifying the font size in qtconfig ruins the colour configuration (even if you don't touch it) and you cannot fix it through qtconfig. So you basically have to change font size in qtconfig, go back to systemsettings5 and re-apply colour setting. This smells like a bug.

---

### Post by speartip on 2018-03-01
I've had problems with fonts in KDE in the past. The way to solve it universally, is to make sure that the GTK font & size in system settings is set the same as your KDE fonts, then run:
```
kdesudo systemsettings5
``` in a terminal & set the fonts & GTK fonts there as well.
Now all fonts should be the same, regardless of what you use.

Basically whatever theme, icons, cursor, fonts you set in system settings, mirror them in "kdesudo systemsettings5" then all your apps should follow the same theme/fonts.

---

### Post by holysword on 2018-03-01
That actually makes me slightly more confused.
I usually configure my root to have a different colour scheme, so that when I am editing a file in a bright red KWrite instance, I know that I'm doing it with root permission. if I log in as root (with su -) and invoke any KDE (4 or 5), it just ignores every change I've made. Now I tried with kdesudo and it worked; the custom root colours apply.

Anyway, your solution would only work if I'd have the same scheme for root and regular users, if I understood it correctly.

---

### Post by speartip on 2018-03-01
No. If you want your root apps to have a red colour scheme, then change your theme to a red one in "kdesudo systemsettings5". But still change your fonts to your user fonts, to keep them consistent.

---

### Post by holysword on 2018-03-02
I guess you did not understand my comment. You cannot have a different font type/size for root and for users with your solution.


Regardless, there is no reason why modifying the settings with one user should affect the settings for another user. Having root settings affect user settings is almost surely a bug.


Moreover, KDE5 applications started under a "su - " environment ignore root scheme settings (all of them, colour and font included) but Qt and KDE4 applications (such as qtconfig, kmix, konqueror) have the proper scheme. It sounds like kdesudo is setting some environment variable that a mere "su - " won't. I've tried checking the output of env of both cases but they seem to match... any ideas?

---

### Post by speartip on 2018-03-02
In that case I reckon it may have something to do with your setup (ubuntu +kde) 
On my setup (plain kubuntu 16.04) you can do what you're trying to do without issue. So it may be that either you have some configuration file conflicting somewhere, or your kde installation is missing some necessary package.

---

### Post by holysword on 2018-03-03
Either that or my computer is acting up for personal reasons; it probably dislikes my new haircut. I knew that it was a mistake!
Jokes aside: of course it is a configuration file or a package (or an environment variable). That has never been the question. The question is: which ones? Where to start digging?

---

