---
title: "Firefly / mt-daapd setup not working"
date: 2006-09-16
forum: Desktop Environments
---

### Post by KeithO on 2006-09-16
I'm trying to set up a Firefly media server.  my system is already a working LAMP server with breezy up to date.  I went through the steps i found [here]("http://dotnet.org.za/matt/articles/48417.aspx") however when I go to [http://localhost:3689](http://localhost:3689), I get an "unable to make connection" error.  I looked in my active services and do not see the daemon listed on there. 

Any ideas?

---

### Post by KeithO on 2006-09-16
bump.

---

### Post by KeithO on 2006-09-17
help me out guys.  i know someone has the answer.

---

### Post by damonkohler on 2006-11-07
My guess is that you're probably not giving it enough time to start up. Do a tail -f /var/log/syslog and wait for mt-daapd to tell you it's finished scanning your songs. Then, you should be able to access the page.

---

