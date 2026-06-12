---
title: "Firestarter blocks internet activity in wine"
date: 2005-12-30
forum: General Help
---

### Post by Mr_J_ on 2005-12-30
I had firestarter just sitting there for a month or so.
Today in the morning i decided to run the wizard and make the firewall run.
I hadn't opened Wine to run Ultima Online that day yet, but it didn't allow the game to verify my account in the program.
Just stood there and no Internet activity was going on.

I found out which IP the server had and which port it used, then i added it to my Incoming servers, and the port to incoming services.

Then i wen't to my outgoing and checked it said permissive by default, so i figured it needed nothing else to allow the connection.

I believe it should be working, since it worked before.

I opened Wine several times and reebooted at least twice threw it all.
I tried to turn off firestarter and restarted wine again. Reebooted, turned off firestarter and tried to use UO in wine again.

My question is! Can I be forgetting something?

I uninstalled firestarter and tried UO in wine again. Reebooted and tried it again. Is there a remote chance i'm forgetting anything?

I had it working behind my routers firewall before, so either the problem is being caused by firestarter or it was a problem with my shard server.
Which i'll check upon getting home.:???: 

Thanks for all the help.
If it continues i'll just format and reinstall Ubuntu.:(

---

### Post by sciurus on 2005-12-31
[QUOTE=Mr_J_]If it continues i'll just format and reinstall Ubuntu.:([/QUOTE]

I would try *sudo apt-get --purge remove firestarter* first.

---

### Post by Mr_J_ on 2005-12-31
What i did worked. Thanks all

---

