---
title: "update-manager service not running"
date: 2006-06-08
forum: Desktop Environments
---

### Post by Ferio on 2006-06-08
Hi, I've just found out that my update-manager service is not running, ¡cos I've launched it and there were some updates. I've been messing up with services to save some RAM, and maybe I've just turned off the one that launched the service. Is it launched by anacron or atd? 'Cos both of 'em are turned off... Thanks in advance!

---

### Post by EReckase on 2006-06-08
I didn't think it was a service - I thought that you just needed update-notifier listed as one of the session startup programs.

E

---

### Post by Ferio on 2006-06-08
I've just had a look and it's on my run-at-the beginning list; it's not working yet, though, but it worked in Breezy. Maybe a bug? All the options seem to be properly set...

---

### Post by Ferio on 2006-06-09
I've found out that it launches by itself when I manually reload the repos in Synaptic. Don't know if it's a clue of what's happening...

---

