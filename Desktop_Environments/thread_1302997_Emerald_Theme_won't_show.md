---
title: "Emerald Theme won't show"
date: 2009-10-27
forum: Desktop Environments
---

### Post by fightforlife on 2009-10-27
I have 9.04 and I had the emerald theme working and then tried to change the panel text color. After a reboot the emerald theme that I really liked, will not show up. I am somewhat new to Ubuntu. It is a great, great operating system, and there's nothing that it can't do so far. I'd just like to get my favorite theme to show up and stay there. The theme is "105399-WhoNeedsW7". What can I do?

---

### Post by mcduck on 2009-10-28
> **fightforlife said:**
> I have 9.04 and I had the emerald theme working and then tried to change the panel text color. After a reboot the emerald theme that I really liked, will not show up. I am somewhat new to Ubuntu. It is a great, great operating system, and there's nothing that it can't do so far. I'd just like to get my favorite theme to show up and stay there. The theme is "105399-WhoNeedsW7". What can I do?

IS Emerald itself actually working? Did you set Compiz to use Emerald as it's default window decorator?

If you didn't, you need to open CompizConfig Settings Manager, and in the Window Decoration-plugin's settings change the "Command"-field to "/usr/bin/emerald". That will make Compiz to automatically start Emerald when you log in.

---

