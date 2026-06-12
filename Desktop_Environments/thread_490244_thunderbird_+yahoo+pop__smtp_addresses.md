---
title: "thunderbird +yahoo+pop / smtp addresses"
date: 2007-07-02
forum: Desktop Environments
---

### Post by Balvinder25 on 2007-07-02
hi all,
         i am a newbie to linux so needed your help on this..i need to download all my yahoo emails to thunderbird..but just cant get it to work..i tried fetchyahoo and freepops but dont know how to link them to the email client..so needed to know the pop and smtp yahoo addresses and by the way i use the free yahoo ac..not a paid one..

---

### Post by milton1 on 2007-07-02
Using the free yahoo, you will need to use thunderbird's webmail plugin

[http://webmail.mozdev.org/](http://webmail.mozdev.org/)

---

### Post by Balvinder25 on 2007-07-02
ok i have the webmail xpi extension installed in thunderbird now what do i do??

---

### Post by milton1 on 2007-07-02
It is in the instructions on the webmail page. You need to set up an account for the yahoo mail; your server must be set to localhost; you will most likely need to open a high-numbered port to localhost to make the plugin function correctly.

[http://webmail.mozdev.org/setup.html](http://webmail.mozdev.org/setup.html)

---

### Post by Balvinder25 on 2007-07-02
hi there for the fast response .sry to be nut but the options that are coming in the link that u showd are some  how different from what i have ..im unable to add the list of domains .when i click on add nothing happens..tried reinstalling the xpi..stil nothing ..??

---

### Post by milton1 on 2007-07-02
did you also add the yahoo webmail plugin? The plugin has two parts; one is required for all web-based mail systems, the other is yahoo-specific. You can check that both are installed, and check the port and domain settings for the plugin by going to tools -> extensions. After that, you must specify localhost as the server when you create an account in thuderbird for yahoo.

---

