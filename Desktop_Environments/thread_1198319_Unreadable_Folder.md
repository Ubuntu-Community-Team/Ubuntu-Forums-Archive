---
title: "Unreadable Folder"
date: 2009-06-27
forum: Desktop Environments
---

### Post by wongpk on 2009-06-27
Good evening all,

Recently I just installed LAMP, to test Wordpress script. I develop a lot of WP themes. Somehow, since it is root access only, everytime I want to add a new theme folder, I use the terminal command "sudo nautilus" to paste my theme folder into it.

After which, I thought it should show in Wordpress admin, it did not. And I check with my user account, it stated that it is unreadable. I do the same again, login as root change all the permission of the folder, it still not showing.

Any help? I am getting really frustrated with it now...

Thanks!

---

### Post by cariboo on 2009-06-27
The directory and files should have either www-data or root as the owner, and the permissions should be set to 755.

---

### Post by wongpk on 2009-07-06
I change my user in root group and it works :P Thanks!!!

---

