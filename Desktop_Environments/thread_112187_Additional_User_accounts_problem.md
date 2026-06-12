---
title: "Additional User accounts problem"
date: 2006-01-03
forum: Desktop Environments
---

### Post by peterx2 on 2006-01-03
Although it is easy to add additional users, it is difficult (if not impossible) to get sudo priveleges for them. Using the instructions in the starter guide doesnt seem to work.

If su is set up while working in the original administrater account, then it is possible to get to su when in an alternative user account. and settings can be made while in bash terminal. but the desktop menus are down the tubes because sudo wont work (I suspect because it is looking for a username/password pair) 

The goal here, as an experiment, is to have the admin user account work in English, and an alternative account work in Estonian. I am looking for estonian menus and openoffice capability as well. I am assuming that Open Office is using the same database files as the system. 

(Since I dont understand Estonian, the project actually is for a friend whom I am trying to help)
pete

---

### Post by Omnios on 2006-01-03
Try going into System/Administratyion/Users and groups. The will be a list of usrs there. Go into user properties and set bin/bash, you can also give user privalages. I havent tryed this as I only have one user set up but this is a place to start.

---

### Post by peterx2 on 2006-01-03
[QUOTE=Omnios]Try going into System/Administratyion/Users and groups. The will be a list of usrs there. Go into user properties and set bin/bash, you can also give user privalages. I havent tryed this as I only have one user set up but this is a place to start.[/QUOTE]

Thanks for the answer...Looking at the list it does say bin/bash in the shell column. The starter help file seems to indicate that sudos can be changed.. by entering in the /etc/sudoers file
"system_username	ALL=(ALL) ALL"
and I went further by making the line say
system_username	ALL=(ALL) NOPASSWD: ALL

Which if this is truly a sudo machine would have eliminated the need for any password. However since this didnt work, it must be that the code taken by the menus is a subroutine somewhere. Does anyone have any ideas.. ??
pete

---

### Post by darth_vector on 2006-01-03
did you

sudo /etc/init.d/sudo restart

after making the changes?

---

### Post by sander marechal on 2006-01-04
Simply checking the "may use administrative tools" checkbox in System >> Administration >> Users and Groups works for me. Don't forget that the second user must use his own password to access the admin tools. E.g. is user_1's pasword is aaaa and user_2's password is bbbb then user_1 needs to enter aaaa for the admin tools, but user_2 needs to use bbbb, not aaaa.

---

### Post by peterx2 on 2006-01-04
[QUOTE=sander marechal]Simply checking the "may use administrative tools" checkbox in System >> Administration >> Users and Groups works for me. Don't forget that the second user must use his own password to access the admin tools. E.g. is user_1's pasword is aaaa and user_2's password is bbbb then user_1 needs to enter aaaa for the admin tools, but user_2 needs to use bbbb, not aaaa.[/QUOTE]

That works... I am very glad that it turned out to be that simple.. Thank you very much. 

The more that I use Ubuntu the more I am impressed with the quality of this distribution.. I have migrated from Knoppix which I have used for years, and this one does appear to be successful at supplying the needs for an enduser desktop. I am now busy inducing friends to try it since it does seem to be more reliable than MS-XP. (which I have on another system for web page construction)
pete

---

