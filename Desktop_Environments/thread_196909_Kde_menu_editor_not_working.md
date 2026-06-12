---
title: "Kde menu editor not working"
date: 2006-06-14
forum: Desktop Environments
---

### Post by [S|G] on 2006-06-14
Hello,

Today I was adding a new program but the kde menu editor isn't saving the changes. Even after I add/remove a program and click on the save icon the changes aren't applied to the menu. I tried to chown and chmod +rw -R my .kde  but didn't seem to have any effect.

---

### Post by GeneralZod on 2006-06-15
Try doing the chown and chmod recursively to

/var/tmp/kdecache-**username**

too.

---

### Post by [S|G] on 2006-06-15
chown and chmod on /var/tmp/kdecache didn't solve the problem either (I did replace username with my user). However I noticed something: this is only happening to submenus and not the menu items themselves.

I managed to get around a duplicate menu entry by deleting all items in a submenu. This did effectively hide it from my panel. However, every time I go to kmenuedit I see the duplicate submenus. Any idea as to what might be the problem?

---

