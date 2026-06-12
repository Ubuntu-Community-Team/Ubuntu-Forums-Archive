---
title: "Deleted mysql 'root' accidently!"
date: 2006-08-30
forum: Desktop Environments
---

### Post by ol1v3r on 2006-08-30
Hello there,

I was playing about with phpmyadmin today and I went to edit the two root accounts but clicked remove instead. So i've been locked out mysql completely.

Luckily no valuable data is in the database so is there any chance someone could walk me through removing and then installing MySQL from scratch?

Thanks! :]

Oli

---

### Post by project46@cia.com on 2006-12-13
Hi I did the same thing myself last week. I had never wrote a linux how to before as im new to linux myself but, Try this. (Note this will delete your mysql database)

Delete all files in /var/lib/mysql
including any folders, I used the rm and rmdir commands

Now run dpkg-reconfigure mysql-server-5.0

This will do its magic and detect that the database needs to be remade etc etc. making the 2 root users accounts for you.

Now it will ask you for root passwords etc, just pressed enter with no password, once this is completed its work, you should beable to login with phpmyadmin again :) 127.0.0.1/phpmyadmin

Good Luck

---

