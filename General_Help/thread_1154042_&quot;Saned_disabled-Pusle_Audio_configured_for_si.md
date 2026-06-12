---
title: "&quot;Saned disabled-Pusle Audio configured for single user session&quot; - Why do I get this?"
date: 2009-05-09
forum: General Help
---

### Post by emarkay on 2009-05-09
On a non-GUI restart or shutdown I see this message, with the [COLOR="Red"]red[/COLOR] asterisk.  
I am getting sound, and notice no issues, but why is Ubuntu flagging this, then?

---

### Post by emarkay on 2009-05-10
Any ideas?

---

### Post by ciaovos on 2009-05-24
I have this problem too.  It also reads "edit /etc/default/saned". 

I found this link helpful in determining whether or not I want to bother to configure sane:
[http://chiralsoftware.com/blog/Linux-network-scanning-with-saned-9404a25b8342ba4e.html](http://chiralsoftware.com/blog/Linux-network-scanning-with-saned-9404a25b8342ba4e.html)

If you are not using a scanner can you simply remove libsane, sane-utils, and xsane (and maybe xinetd if it is installed) in order to solve the problem?

---

### Post by antarezx on 2012-12-25
hi, to solve your problem you have to do this:
When it displayed the problem you need to follow these steps:
admitted to one of the seven physical terminal with:

ctrl + alt + F1  (to exit press ctrl + alt + F7)

Then it will ask for your user name:

$ User

(you hit ENTER)

Then it will ask the password of your account

$ *******

(you hit ENTER)

and are now signed through the terminal to your account, you will be something like:

User@user-pc:~$

After you enter this command:

$ sudo apt-get remove libsane

It will ask for the password:

$ ********

and execute the uninstallation.

After running this command to restart the PC

$ sudo shutdown-r now

then wait a little and its fixed. :]

Sorry for my bad english....

---

