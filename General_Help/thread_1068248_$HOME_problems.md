---
title: "$HOME problems"
date: 2009-02-12
forum: General Help
---

### Post by Torille on 2009-02-12
Hi,Recently i had configured my VBox (Win XP) to synchonized mi ipod on Ubuntu but after that when I had logged on to Ubuntu show the following message:

"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved file should be owned by user and have 644 permisions. User's $HOME directory must be owned by user and not writable by other users"

I don't know what it happened really, i just did to user root be available y my user changed permisions with sudo chmod 777 but i don't really think that made happen this error..

Did i have to change my permisions ,again?? or what should i have to do??

This problem had had to my perfomance is very low now...

---

### Post by The Cog on 2009-02-12
Try this command to delete the file:
```
rm ~/.dmrc
```
The file will get recreated as needed.

---

