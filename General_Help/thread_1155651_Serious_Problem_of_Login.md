---
title: "Serious Problem of Login"
date: 2009-05-11
forum: General Help
---

### Post by Imran83 on 2009-05-11
Hi, I am New in Ubuntu so, i have done something wrong.

Now the Problem is that i have a account named "imran" (this is created on installation) and i have add the following line in the /etc/group file 

 admin: X :117:imran,domainuser

my system is on domain and this line cause problem for me i am unable to login with user "imran" and i have a just user its has not administrative rights now what i do to gain the administrative right and remove the above line from /etc/group 


plz help

---

### Post by hw-tph on 2009-05-11
Booting into single user mode will let you edit your passwd and group files. To do this, simply append the word "single" (without quotes) to your kernel command line in Grub and boot. You will not be able to access your network or use graphical mode in single user mode.

---

### Post by Imran83 on 2009-05-11
Thanks

---

