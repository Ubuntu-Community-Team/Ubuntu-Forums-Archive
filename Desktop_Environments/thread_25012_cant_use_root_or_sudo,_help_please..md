---
title: "cant use root or sudo, help please."
date: 2005-04-08
forum: Desktop Environments
---

### Post by cstaff on 2005-04-08
ok so i'm really new to linux and after like 2 weeks of trying distos I have settled on Kubuntu.  so anyways, to my problem.  Everytime i try to use something that requires root permissions i enter the password into the box and then recieve this error "Conversation with su failed.".  So then I tried going into the terminal and using the sudo command. Just as an example i did.

cstaff@staff:~$ sudo apt-get update
Password:
cstaff is not in the sudoers file.  This incident will be reported.
cstaff@staff:~$

i enter the password but nothing shows up in the box, so im not sure if it's getting the password.

so if theres anything anyone could recomend to help me, it would be much appreciated.

thnx,
cstaff

---

### Post by bored2k on 2005-04-09
[http://ubuntuguide.org/4.10/index.html#gainrootwithoutlogin](http://ubuntuguide.org/4.10/index.html#gainrootwithoutlogin)
That should help you on resetting your su password.

---

### Post by cstaff on 2005-04-09
thnx but that didnt help.  is there anyway i could login to the root using the GUI?

thnx
cstaff

---

### Post by devil28 on 2005-04-09
you could try sudo -s or sudo -i
normaly your user that you created during install should be in sudoers list. if you created a new user, you will have to add that to the list.

---

### Post by cstaff on 2005-04-09
how would i go about accessing the list?

thnx
cstaff

---

### Post by sjalex on 2005-04-09
[QUOTE=cstaff]how would i go about accessing the list?

thnx
cstaff[/QUOTE]
You access the list by using sudo, so maybe that's not good advice... do you have just the default account you created on your machine? Or did you create additional accounts? The initial account you created when you installed should have access to use sudo.

If it doesn't, you should be able to use the link provided above. You said that didn't help, but what did you do? If you ran the chroot command, you should then do 'less /etc/sudoers' and make sure there's a line in there that says '%admin ALL=(ALL) ALL'. If there is, quit out of 'less', do 'vigr', find the line that says "admin:x:109:" or something similar and append your user name (do you know how to use vi? separate topic but for your purposes here you can just put your cursor on the "admin:" line with the arrow keys, type a capital "A", then enter your user name, type the escape key, then ":wq!" to save the file) so it says "admin:x:109:username". That should do it for you.

As long as you're in the CD-root mode, you can do 'passwd' as well which will give you the opportunity to set the root password outright. If you do that then you can login to the system as root, or use the su command to gain root access.

---

