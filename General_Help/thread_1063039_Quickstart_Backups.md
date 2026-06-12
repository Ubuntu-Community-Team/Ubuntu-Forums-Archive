---
title: "Quickstart Backups"
date: 2009-02-07
forum: General Help
---

### Post by terry_gardener on 2009-02-07
hello 

i am using quickstart to backup my home directory on an weekly basis, but it is creating a new backup file every time. 

how do i get it to delete the old scheduled backup before creating the new backup file.  

it is backing up fine but this would just save me from deleting the files manually.

---

### Post by terry_gardener on 2009-02-07
might have solved this, wont know until next scheduled backup which is tomorrow. 

what i have done is edited the my scheduled backup file with the cron folder in the home folder and added line "rm tar_home_backup*" before the tar line. 

i have already deleted the other 2 tar lines because i only wanted to backup the home folder. 

i think this should delete the old backup and then create the new backup.

i will mark this thread tomorrow as solved if this works.

---

### Post by terry_gardener on 2009-02-08
the above worked and this is now solved.

---

### Post by gandalf2000 on 2009-03-10
Thank you for this, Terry.  Just what I was looking for.

---

