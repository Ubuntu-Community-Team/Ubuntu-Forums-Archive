---
title: "How do I reset /usr permissions to the linux default?(I accidently changed it)"
date: 2009-06-14
forum: General Help
---

### Post by hamid11 on 2009-06-14
Hi all.
I'm new to ubuntu.I ran this command:
sudo chmod 777 -R /usr
Now there are a lot of problems.
Is there any way to reset permissions to default?

THanks

---

### Post by mikewhatever on 2009-06-14
Can you post the output of **ls -l /usr**.
I suppose running chmod -R 755 should reset most of the files to their default permissions

---

