---
title: "Reset &quot;Send Link&quot; in Firefox 4 Thunderbird"
date: 2009-04-27
forum: General Help
---

### Post by sandman3838 on 2009-04-27
Hello

Every time I select "Send Link" in Firefox 3.0.9 I get GMAIL Window.

See the attached screen shot!

So far I have tried this several times: 

------------------------- 
In Firefox's Location (URL) Bar, enter:

Code:

about:config

Then press <enter> or click "Go".

With the cursor in the body of the resulting page, <right-click> the mouse.

From the pop-up menu, select "New".

From the next pop-up menu, select "String".

In the pop-up dialog box "Enter preference name", enter:

Code:

network.protocol-handler.app.mailto

Then click "OK".

In the pop-up dialog box "? network.protocol-handler.app.mailto", enter:

Code:

/usr/bin/mozilla-thunderbird

Then click "OK".

----------------------------  

Also in Ubuntu 9.04 SYSTEM/PREFERENCES/PREFERED APPLICATIONS
mozilla-thunderbird
is selected!

Has anyone else had issues with this?

Thank you for your time and help!

---

### Post by kanikilu on 2009-04-28
In Firefox, try going to Edit > Preferences > Applications, you should see "mailto" listed under the content types. See if you can change the action to use thunderbird.

---

### Post by sandman3838 on 2009-04-28
Been there tried that.
What I did above in my intro was to place an entry for Thunderbird in the "MAILTO" option in Firefox. (Edit > Preferences > Applications)

Would you or anyone else have any suggestions?

---

### Post by sandman3838 on 2009-04-28
Got it!
I just sat down and started looking around.

If you have "Google Toolbar" installed with GMAIL selected in Google Options it overrides you default Email program in Firefox.  Just uncheck it!


Thanks for your help.

---

### Post by eudemus on 2009-06-04
Check out also this thread
[http://ubuntuforums.org/showthread.php?t=860010&page=2](http://ubuntuforums.org/showthread.php?t=860010&page=2)

Worked for me when nothing else did.
Basically Firefox 3 doesn't use this "network.protocol-handler.app.mailto" thing any more, but if you've upgraded from Firefox 2, you'll have a load of config data set up for it, which seems to confuse Firefox.

Anyway, that thread tells you how to sort it out.
Cheers,
Eudemus

---

### Post by eudemus on 2009-06-04
This may be relevant as well:

Check out also this thread
[http://ubuntuforums.org/showthread.php?t=860010&page=2](http://ubuntuforums.org/showthread.php?t=860010&page=2)

Worked for me when nothing else did.
Basically Firefox 3 doesn't use this "network.protocol-handler.app.mailto" thing any more, but if you've upgraded from Firefox 2, you'll have a load of config data set up for it, which seems to confuse Firefox.

Anyway, that thread tells you how to sort it out.
Cheers,
Eudemus

---

