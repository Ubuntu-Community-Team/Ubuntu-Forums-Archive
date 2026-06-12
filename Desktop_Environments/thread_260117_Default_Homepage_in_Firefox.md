---
title: "Default Homepage in Firefox?"
date: 2006-09-18
forum: Desktop Environments
---

### Post by bmkrein on 2006-09-18
Question abut firefox customization.

I am tryieng to change the Firefox default homepage  for my computer class users. 
I did edit firefox.js in default/pref directory in way i knew, but no result... 
I searched also forums but not yet result... Seems it is so easy that everybody knows. I did not find How-to's about this eather. #-o 

Would be clad , ff somebody knows... 

-ReinL:

---

### Post by nikhilk on 2006-09-18
Cant you do it from Edit->Preferences menu. In the General tab the first option is for setting the default home page.

---

### Post by edm1 on 2006-09-18
can you not just go to Edit->Preferences->General in firefox and change it?

---

### Post by emale07 on 2006-09-18
Edit -> Preferences

Under the general tab, edit the "location" to whatever page ou want.

---

### Post by moore.bryan on 2006-09-18
[I]if you're trying to do it en-masse, create the user.js file and put in ```
user_pref("browser.startup.homepage", http://www.whateverpage.com);
``` having the address what you want it to be. then put the new user.js file in the preferences folder on all your machines.
[/I]

---

### Post by bmkrein on 2006-09-18
> **moore.bryan said:**
> [I]if you're trying to do it en-masse, 
[/I]
Yes, my need for to do it system-wide. For one user it is easy, sure. 

I tried this now. But no result. 

Also i tried 

In /usr/lib/firefox/defaults/pref file firefox.js 
I changed there
[INDENT][FONT="Fixedsys"]pref("browser.startup.homepage",	          "chrome://browser-region/locale/region.properties");[/FONT][/INDENT]

To 
[INDENT][FONT="Fixedsys"]pref("browser.startup.homepage", "http://www.google.com");[/FONT][/INDENT]

But also no result... 

I found soulution !!!

With changing 
/usr/lib/firefox/firefox.cfg file 
To
[INDENT][FONT="Fixedsys"]pref("browser.startup.homepage", "http://www.google.com");[/FONT]
[/INDENT]

Thanks

-ReinL:

---

### Post by moore.bryan on 2006-09-18
*i'm glad it worked for you... for future note, mozilla suggests not editing the pref.js file directly.  when you add a user.js file, firefox just looks there first for settings before moving onto the pref.js file.  i'm confused why the firefox.cfg file mattered...*

---

