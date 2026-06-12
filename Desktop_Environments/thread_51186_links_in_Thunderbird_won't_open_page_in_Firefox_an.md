---
title: "links in Thunderbird won't open page in Firefox and vice versa"
date: 2005-07-22
forum: Desktop Environments
---

### Post by Loungefly on 2005-07-22
Hey all :)

I'm having a problem that I am totally stumped on.

I'm using Thunderbird (which i installed from the Ubuntu repos) and Firefox (which I took from mozilla.org  to get rid of the Gnome "save as" dialogs etc).

Whenever I click a link in an email in Thunderbird that's supposed to open a page in Firefox, nothing happens. I can't even get the "Get New Themes" link in the theme manager to open the themes page at mozilla.org. Also, "mail to" links in Firefox that should open Thunderbird don't work either.

I've gone into Control Panel--->KDE Componenets----> Compoenent Chooser and set Thunderbird and Firefox as the default email and browser app and that doesn't help at all.

Would anyone know how I might be able to fix this?

I'd greatly appreciate any help with this. I'm pulling my hair out! ](*,)

---

### Post by dave9191 on 2005-07-22
This might help :) 

[http://forums.mozillazine.org/viewtopic.php?t=295536](http://forums.mozillazine.org/viewtopic.php?t=295536)

Dave

---

### Post by Loungefly on 2005-07-22
Nah, I checked the wiki earlier and it didn't have anything relating to it.  :-|  Thanks anyway :smile: 

I managed to find the solution on another site. I just posted a "How To" in Tips & Tricks if anyone else is having similar problems

[http://www.ubuntuforums.org/showthread.php?t=51206](http://www.ubuntuforums.org/showthread.php?t=51206)

---

### Post by chandra on 2005-07-23
Subject: Firefox-Thunderbird Integration
Acknowledgement: Ubuntu Forums: [http://ubuntuforums.org/showthread.php?t=22333&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=22333&page=1&pp=10)
--------------
Purpose: Click on a mailto: link in Firefox to open that link in Thunderbird

Distribution/OS: Kubuntu Linux

HowTo:

1. cd ~/.mozilla/firefox/<SomeString.default>

2. If the file user.js does not exist, create it.

3. Append the following lines to the file:

//Firefox-Thunderbird mailto: Integration
user_pref("network.protocol-handler.app.mailto","/usr/bin/mozilla-thunderbird");

4. Close and restart Firefox, and test functionality.
--------------
Purpose: Click on an http: link in Thunderbird to open that link in Firefox

Distribution/OS: Kubuntu Linux

HowTo:

1. cd ~/.mozilla-thunderbird/<SomeString.default>

2. If the file user.js does not exist, create it.

3. Append the following lines to the file:

// Thunderbird-Firefox http: Integration
user_pref("network.protocol-handler.app.http", "/usr/bin/mozilla-firefox");

4. Close and restart Thunderbird, and test functionality.

---

### Post by dave9191 on 2005-07-23
[QUOTE=Loungefly]Nah, I checked the wiki earlier and it didn't have anything relating to it.  :-|  Thanks anyway :smile: 

I managed to find the solution on another site. I just posted a "How To" in Tips & Tricks if anyone else is having similar problems

[http://www.ubuntuforums.org/showthread.php?t=51206](http://www.ubuntuforums.org/showthread.php?t=51206)[/QUOTE]


Sorry, I seem to forgot to paste the link into my post (it was late last nite). 

This is the link that was supposed to be there:

[http://forums.mozillazine.org/viewtopic.php?t=295536](http://forums.mozillazine.org/viewtopic.php?t=295536)

Dave

---

