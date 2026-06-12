---
title: "sun-j2re1.5 does not affect konqueror"
date: 2005-09-04
forum: Desktop Environments
---

### Post by daller on 2005-09-04
Hi All,

Installing the package sun-j2re1.5 automatically enables java i mozilla og mozilla-firefox, but how do I activate it in konqueror?

As far as I know, konqueror is set to use mozilla's plugins as default?

Please help!

---

### Post by arjaybe on 2005-09-04
[QUOTE=daller]Hi All,

Installing the package sun-j2re1.5 automatically enables java i mozilla og mozilla-firefox, but how do I activate it in konqueror?

As far as I know, konqueror is set to use mozilla's plugins as default?

Please help![/QUOTE]
 In Konqueror go to Settings/Configure Konqueror/Java & Javascript and the first page tells Konqueror where to look for Java.  It does use Mozilla plugins but Java isn't a plugin.

---

### Post by daller on 2005-09-04
Thanks, it works perfectly now - except for one thing though!

My webbank-page tells me that my browser doesn't support session-cookies - is there anything to do about that?

---

### Post by arjaybe on 2005-09-04
[QUOTE=daller]Thanks, it works perfectly now - except for one thing though!

My webbank-page tells me that my browser doesn't support session-cookies - is there anything to do about that?[/QUOTE]
 Did you try Cookies under Settings?

---

### Post by daller on 2005-09-05
Yes, and they are activated - per default!

---

### Post by arjaybe on 2005-09-05
[QUOTE=daller]Yes, and they are activated - per default![/QUOTE]
 Then maybe the site is wrong.  Try changing your browser identification (Tools/Change Browser Identification) in case the site is looking for some specific browser types.

Is the error at a stage in your use of the site where I could check it out?  Or is it after you log in?

---

### Post by daller on 2005-09-06
I can't login... (In mozilla I can!)

[https://www.ringkjoebing-bank.dk/webbank/webbank.htm](https://www.ringkjoebing-bank.dk/webbank/webbank.htm)

At the bottom of the page, I see this message:

"Din browser understøtter ikke sessions cookies - Klik her for hjælp"
Which means:
"Your browser does not support session cookies - Click here for help"
Clicking the link, tells me to upgrade to IE6.0 - Which is not preferable :)

Trying to login, gives me this message:

---
Siden kan ikke vises, fordi oplysningerne er forældede.
Foretag venligst et valg i menuen.
---

Translated into english:

---
The page can not be displayed, because some information is outdated.
Please make a choise in the menu.
---

Telling Konqueror to act as "IE6 on XP" doesn't help anything...

If you want to test it yourself, here is my information:

user (Brugernummer): 76562069179

Please select the radio-button "Jeg har anvendt WebBank før" - which means that the key is already on the harddisc! (In your case it isn't, but it will spare you the time to read how to activate it - In danish :))

---

### Post by arjaybe on 2005-09-06
I couldn't get it to work using any browser identification in Konqueror.  I guess you could use Mozilla for that site.

---

### Post by daller on 2005-09-07
Mozilla handles it just fine... guess I have to keep using mozilla then...

---

