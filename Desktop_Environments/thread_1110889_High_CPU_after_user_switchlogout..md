---
title: "High CPU after user switch/logout."
date: 2009-03-30
forum: Desktop Environments
---

### Post by AintJoe on 2009-03-30
I recently added a user account to my desktop for my girlfriend. She uses my computer when Im not there to check her e-mail and such.

Whenever she switches to her account and then logs off, my processor spikes from leftover processes on her account. 

I have to run
```
sudo pkill -u kathleen
```
to make it stop. 

Seems like this command should already be in the logout procedures.

How can I fix this?

---

