---
title: "Connect To Server | Windows Share not in file system"
date: 2010-07-28
forum: Desktop Environments
---

### Post by chrisstankevitz on 2010-07-28
I used this method to connect to a windows computer:
  Places | Connect To Server | Windows Share | xxx

The share appears here:
  Places | Computer | xxx

However, it does not appear on my filesystem in /media/xxx

Question 1: where on my filesystem does this mount appear?

Question 2: If it does not appear in my filesystem, how can I get it there?

Thank you,

Chris

---

### Post by Morbius1 on 2010-07-28
/home/your_user_name/.gvfs/share_name on server_name

---

### Post by chrisstankevitz on 2010-07-28
thank you

---

