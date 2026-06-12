---
title: "[SOLVED] Language does not appear in Login Window Language Selection?"
date: 2008-04-20
forum: Desktop Effects &amp; Customization
---

### Post by gobi on 2008-04-20
I installed new language pack (Mongolian). Installation went with no any errors and I am seeing added language in language support settings.

But when I login I dont see the language in language selection in gnome login windows.

So I tried by setting in  /etc/environment as following
```

LANG="mn_MN.UTF-8"
LANGUAGE="mn_MN:mn"

```

Then language is changed successfully.

But I want to make it possible to choose language when I login.

Could someone teach me pleaze?

---

### Post by erginemr on 2008-04-21
You can try the steps in the attached screenshots. However, I have also tried to add Mongolian to my system with no avail. It seems to have no effect in the application menus at all.

There are two locations in Ubuntu, where language settings are kept:
**/etc/environment** & **/etc/default/locale**

and the command from the terminal:
```
locale
```
should report correctly. 

Yet again, my attempts have been unsuccessful. Good luck...

---

### Post by gobi on 2008-04-21
Thank you Ergin

The screenshots are exactly what I did. And the result is exactly same. Anyway it looks the problem is faced not only to me ;)

I still could not solve the problem :(

---

### Post by gobi on 2008-04-26
After I upgrade my distro problem has disappeared

---

