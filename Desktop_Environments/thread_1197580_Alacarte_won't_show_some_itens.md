---
title: "Alacarte won't show some itens"
date: 2009-06-26
forum: Desktop Environments
---

### Post by fcmartins on 2009-06-26
Hello,

I'm running Ubuntu 8.04. When I run alacarte using my regular user, some itens (jockey, synaptic) will show with a small italic font. If a select the item, it will remain checked for a few seconds and then it unchecks itself.

If I add my user to the root group, the itens will look alright in alacarte and they'll show up in the Administration menu. After I remove my user from the root group the problem returns.

There's a few topics from people with similar problems, but none of them solved mine.

---

### Post by billgoldberg on 2009-06-26
What can I say?

Run it with **gksu alacarte**.

---

### Post by mcduck on 2009-06-26
> **billgoldberg said:**
> What can I say?

Run it with **gksu alacarte**.

That wouldn't help, as it would result in editing the root user's menu, not the normal user's..

(and if it edited the normal user's menu, it would mean overwriting the user's menu configuration files with root permission, pretty much breaking the menu completely for that user)

Does your user belong to admin group? Synaptic is admin tool and it only makes sense if normal users (without admin rights) can't enable it in their menus as they wouldn't be able to use it anyway..

---

### Post by fcmartins on 2009-06-26
> **mcduck said:**
> Does your user belong to admin group? Synaptic is admin tool and it only makes sense if normal users (without admin rights) can't enable it in their menus as they wouldn't be able to use it anyway..
Thanks, you nailed it. My user had sudo powers but wasn't in the admin group. =D>

---

