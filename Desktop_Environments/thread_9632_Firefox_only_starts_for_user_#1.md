---
title: "Firefox only starts for user #1"
date: 2004-12-30
forum: Desktop Environments
---

### Post by mal on 2004-12-30
I have a problem with Firefox on a Warty machine.  After an apt-get upgrade and the installation of various applications, including mplayer, I now find that firefox will only run for the admin user (me).  For all other users it just silently dies during the start-up process.

I would appreciate it if anyone could suggest where I should start looking to solve this problem.

Mal

---

### Post by martinlk on 2004-12-30
Try deleting the profile directory for all users. Can't remember if it's ~/.firefox or ~/.mozilla

---

### Post by mal on 2004-12-30
Great - that did the trick.   =D> 

The user  profile directories are ~/.mozilla.  Renaming them allowed firefox to start up and it created a new user profile.

Thanks for the suggestion.

Regards,

Mal

---

