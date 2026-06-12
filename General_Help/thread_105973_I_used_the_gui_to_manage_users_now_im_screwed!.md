---
title: "I used the gui to manage users now im screwed!"
date: 2005-12-19
forum: General Help
---

### Post by d33psix on 2005-12-19
I used the gui to manage my users on the system.
I created a user with admin priveleges and removed the admin priveleges from the initial user account. clicked ok and now i dont have admin priveleges from either account.

i type id at the command prompt and it says i have admin priveleges but when i sudo apt-get or other commands the program doesnt respond i dont get errors or anything just another command prompt. none of the admin gui programs work anymore.

any help would be appreciated

---

### Post by amohanty on 2005-12-20
Can you post the **_exact_** steps you took to do this?

AM

---

### Post by d33psix on 2005-12-20
[QUOTE=amohanty]Can you post the **_exact_** steps you took to do this?

AM[/QUOTE]

System->Administration->Users and Groups->add user->fill in the Account info->click the user priveleges tab->fill the check box for Executing system administration tasks->click ok 

then select the default user u installed ubuntu with and click the properties button->then click the user priveleges tab->uncheck the check box for Executing system administration tasks->click ok


how ever prior to doing the above i deleted an already added user named umpitysquat i had set up earlier(who didnt have admin priveleges).
after removing the user with the gui the home directory of the user wasnt removed and the remaining upitysquat dir became the new admin privelged guys directory but when logging in and out of gnome this causes problems because the username doesnt match the home directory name.

and to top it all off if you do this in the order i did it you wont have admin priveleges to rename the directory of the new priveleged user and the new priveleged user isnt added to the sudoers list so he cant rename it either typing id on the terminal shows that the user has admin priveleges but sudo, su, gksudo, and visudo dont work for either of the accounts.

I had to reinstall completely

---

### Post by markcaetano@gmail.com on 2005-12-20
ha ha mr hack hack

sorry to hear bout your problem
try this

when it first boots in text mode and it says "[FONT="Lucida Console"][/FONT][FONT="Lucida Console"]Grub Loading Press esc to enter[/FONT]
do this as soon as it appears as it happens right after the POST is complete
if u miss it u will have to reboot
when u r in the grub select
[FONT="Lucida Console"]Ubuntu kernel 2.6(recovery mode)[/FONT]
press enter and hope for the best

good luck

mark

---

### Post by az on 2005-12-20
[QUOTE=markcaetano@gmail.com]ha ha mr hack hack
[/QUOTE]

Not a very nice thing to say.

[QUOTE=markcaetano@gmail.com]
sorry to hear bout your problem
try this

when it first boots in text mode and it says "[FONT="Lucida Console"][/FONT][FONT="Lucida Console"]Grub Loading Press esc to enter[/FONT]
do this as soon as it appears as it happens right after the POST is complete
if u miss it u will have to reboot
when u r in the grub select
[FONT="Lucida Console"]Ubuntu kernel 2.6(recovery mode)[/FONT]
press enter and hope for the best

good luck

mark[/QUOTE]

Look in your /etc/sudoers file

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

Make sure that is there.  Then, look in /etc/group and make sure your username is listed in admin

admin:x:106:sam

reboot


You edit files with nano

sudo nano /etc/group

---

