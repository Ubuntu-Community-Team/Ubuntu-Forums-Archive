---
title: "date &amp; time sync on dapper 6.06"
date: 2006-04-22
forum: Desktop Environments
---

### Post by wpshooter on 2006-04-22
I could not get the time clock sync function (the repeative one) to work under 6.06 like I used to under 5.10.

I had to change to root user and give root user rights to perform admin. functions in order to get the time and date sync function to work.

Am I doing something wrong or is this the way it is supposed to work NOW ?

Thanks.

---

### Post by jongkind on 2006-04-23
More people experience the same problems, including me. I do it by hand:

sudo ntpdate ntp.ubuntu.com

Herman

---

