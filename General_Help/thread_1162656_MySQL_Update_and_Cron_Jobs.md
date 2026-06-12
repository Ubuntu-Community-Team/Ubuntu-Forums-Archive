---
title: "MySQL Update and Cron Jobs"
date: 2009-05-17
forum: General Help
---

### Post by abasel on 2009-05-17
I have never done any scheduling in Linux but gather that the Cron jobs are where it happens :-)

I want the following MySQL update to be done once a day, so as to ensure that my student's e-mails are correctly maintained:

UPDATE mdl_user SET email= CONCAT(username,'@student.school.nz') WHERE ((length(username) =4) and !(email LIKE '____@student.school.nz') and (length(email)>0))

How do I do this?

---

