---
title: "hide thunderbird inbox"
date: 2009-06-17
forum: General Help
---

### Post by ZeldaFan on 2009-06-17
Is there a way to password Mozilla Thunderbird such that not just incoming messages are blocked, but my entire inbox viewing is blocked unless a password is entered?

---

### Post by maheshasolkar on 2009-06-17
Following should be of some help:

  [http://kb.mozillazine.org/Protecting_the_contents_of_the_profile_-_mail](http://kb.mozillazine.org/Protecting_the_contents_of_the_profile_-_mail)

Following shows how TrueCrypt can be used to protect your profile content. Granted, not the most elegant way, but if it works, it is pretty secure:

  [http://linuxnewb.wordpress.com/2008/01/29/encrypt-thunderbird-profile-with-truecrypt-in-linux/](http://linuxnewb.wordpress.com/2008/01/29/encrypt-thunderbird-profile-with-truecrypt-in-linux/)

I have not used the above myself. I am just trying to point you to possible solutions.

---

### Post by John Bennett on 2010-03-17
[COLOR="Indigo"]Password protect the message pane (IMAP only)[/COLOR] 

With this trick, Mozilla Thunderbird will password protect the message list pane (aka the thread pane) by keeping it blank until you log in and enter a password for that account. 

In the Config Editor, search for the preference *mail.password_protect_local_cache*, and change its value to **true**.


[COLOR="Indigo"]Config Editor[/COLOR]

To access the Config Editor, go Edit > Preferences, select the Advanced options panel, and click on Config Editor.

---

