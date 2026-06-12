---
title: "Installing Flash/Shockwave on another user login."
date: 2005-10-31
forum: Desktop Environments
---

### Post by Darrin on 2005-10-31
I set my wife up with a username. For some reason flash or shockwave plugins are not installed for firefox on that particular user name. I have a couple questions here. How do I get flash or shockwave installed while on her account?
How do I access Add Applications on her account (It askes for a password, but mine doesnt work)

---

### Post by jmcnaught on 2005-11-01
hi,

if flash is installed and it works for one user, it should work for another user. does flash get listed when you go to about: plugins (remove the space between the colon and plugins) in firefox on your wife's account?

Add Applications (and most of the stuff under system>admin) are only available to users in the *admin* group.

How did you create your wife's account, on the command line or in the Users and Groups tool from system>admin? I would suggest checking her privileges there. Putting a checkmark beside "Executing system administration tasks" would add her to the *admin* (and hence be able to run tools under system>admin). If she's not going to be installing new programs and creating new accounts etc, she doesn't need that turned on. **Note** above.. you don't need to install flash again if it already works for other users on the computer.

You could try removing the mozilla hidden folder in her home folder and starting Firefox again.  Go to the home folder in Nautilus, click View > Show Hidden Files.  Locate the folder called .mozilla (files/folders that begin with a . are "hidden").  Rename that folder to something else (if you want to be able to restore it, or salvage her bookmarks.html from it).  Start Firefox.  It will run as though it was running for the first time and create a new .mozilla folder.

hope that helps.

jeremy mcnaughton

---

### Post by Darrin on 2005-11-01
Thanks for the response. She hasnt been logged in since my post. I went to login to her account to start going over your instructions. First I tested the site which said the plugin was needed, this time it worked.. go figure. I dont know what happened, but it works now. Thanks for the help though. :smile:

---

