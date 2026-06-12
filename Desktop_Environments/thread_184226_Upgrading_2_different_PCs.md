---
title: "Upgrading 2 different PCs"
date: 2006-05-29
forum: Desktop Environments
---

### Post by Aramil on 2006-05-29
Hi! I have 2 Pcs running Ubuntu 5.10.AS we all know in a few days Dapper Drake final version is coming out.Is there a way downloading the upgrade once and use it in both computers?The upgrade will be done via Synaptic or by CD?And one last question.Will the upgrade delete breezy badger's files?Cause I dont have much space....:p

---

### Post by Ramses de Norre on 2006-05-29
You could download the iso, burn it and use apt-cdrom add to add it to your sources, then run sudo aptitude update && sudo aptitude dist-upgrade as usual. You'll need to download only one iso for both machines then.

---

### Post by Aramil on 2006-05-29
omg i m so stupid......I didnt think that......So easy...Thank you!

---

### Post by Aramil on 2006-05-30
What about the breezy files?Will they remain or the upgrade will delete them?

---

### Post by aysiu on 2006-05-30
When you download the ISO, be sure to get the alternate install CD.

The desktop CD will not have any packages for upgrading--it's for straight installation only.

And your files will be safe, but none of your Breezy packages will remain--they'll all be upgraded to Dapper packages.

---

