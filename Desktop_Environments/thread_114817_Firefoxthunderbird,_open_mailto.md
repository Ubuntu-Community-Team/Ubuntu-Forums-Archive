---
title: "Firefox/thunderbird, open mailto:"
date: 2006-01-09
forum: Desktop Environments
---

### Post by DrSkalpell on 2006-01-09
Hi.

When I click on a mailto: (email link) both thunderbird and the "compose to" window open. I would like just the "compose to" window to open when I click on a mailto: (like it is by default in windows) . Is this possible and how?

Firefox 1.0.7
Thunderbird 1.0.7
Preferred email client: Thunderbird

Btw I searched the database but could not find an answer...

---

### Post by rfruth on 2006-01-09
I don't think its possible, for the compose window to open Tbird needs to be running -
I used Tbird (1.0.7) with XP & it was the same way (configured wrong) Lookout (er Outlook or OE might do this) :rolleyes:

---

### Post by mad_phoenix on 2006-01-17
However, even when Thunderbird is already open, Ubuntu opens a new instance of it and a new compose window for mailto: links.  

This has been really frustrating for me, as a web developer I want to test these links without closing two windows every time, or dealing with lots of open instances of thunderbird.

Is there really now way to do this?

P.S. I've tried this using both 1.0.7(default Ubuntu Breezy) and 1.5 (installed to /opt).  Neither works, unfortunately.

---

### Post by mustang on 2006-01-17
That's weird because when I click on a mailto link, only the compose window opens. I still have the thunderbird that shipped with Ubuntu Breezy and I have not touched any other settings.

---

### Post by 12quality on 2006-01-28
The same thing has been happening to me since I installed Thunderbird 1.5.  It did not occur when Thunderbird 1.07 was installed. (I am using Firefox 1.5).

---

### Post by 12quality on 2006-01-28
I just found the solution to this problem.  Follow the instructions at [this post]("http://ubuntuforums.org/showpost.php?p=375841&postcount=3").  

Basically, edit about:config page and add the entry ```
network.protocol-handler.app.mailto
``` and give it the value ```
thunderbird
```

I haven't tried other suggestions, which are much more complicated and suggest editing user.js.  But why waste your time when this answer is so simple?

---

### Post by sundman on 2006-01-31
Also check System - Administration - Prefered programs. Changing the email application command to 
```
mozilla-thunderbird -compose %s
```
seems to work. The default switch "-mail" brings up the profile selection window if an instance of thunderbird is already running.

---

### Post by mlissner on 2006-02-07
This worked like a charm for me too. Thank god.

---

### Post by nanotube on 2006-02-07
cool, the -compose trick made it work for me too. :)

---

