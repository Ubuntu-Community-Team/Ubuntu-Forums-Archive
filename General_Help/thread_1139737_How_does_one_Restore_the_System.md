---
title: "How does one Restore the System?"
date: 2009-04-27
forum: General Help
---

### Post by shuukazedojo on 2009-04-27
Well, it looks like I may have messed things up beyond my level of expertise to fix. I was wondering where the Restore System ap went in 8.10. I found this, [https://wiki.ubuntu.com/SystemRestore](https://wiki.ubuntu.com/SystemRestore)
but I can't tell if this is something that used to exist and doesn't anymore or if it is an idea to implement. 

I tend to think it used to exist since it gives navigation to the ap under System > Administration. 

In any case, I have not backed up any data yet and would like to restore my system to 2 days ago. Is this possible and how? If this is not possible, why has it not been made possible? 

Thanks!

---

### Post by aaronp on 2009-04-27
> **shuukazedojo said:**
> Well, it looks like I may have messed things up beyond my level of expertise to fix. I was wondering where the Restore System ap went in 8.10. I found this, [https://wiki.ubuntu.com/SystemRestore](https://wiki.ubuntu.com/SystemRestore)
but I can't tell if this is something that used to exist and doesn't anymore or if it is an idea to implement. 

I tend to think it used to exist since it gives navigation to the ap under System > Administration. 

In any case, I have not backed up any data yet and would like to restore my system to 2 days ago. Is this possible and how? If this is not possible, why has it not been made possible? 

Thanks!


Not sure about the restore system option in Ubuntu but a live system resuce CD might do the trick. 

[www.sysresccd.org](www.sysresccd.org)

If you can't fix the problems you have, you might get away with mounting your drives and retrieving your data before you start fresh.

---

### Post by shuukazedojo on 2009-04-27
Thanks for the reply. Thankfully, I didn't need to do any of that. My HD was full and was creating some new and interesting issues. I reduced the load and PRESTO! 

I DO think that a function like Winbloze System Restore should be added, though. Like the wiki entry I posted before says, it encourages people to do more with their computer without fear of never being able to return safely.

---

### Post by cariboo on 2009-04-27
A good backup strategy will beat a system restore any time.

---

### Post by Seventh Reign on 2009-04-27
Windows system restore never worked anyway.  Its just a drive-space hog.

---

### Post by aaronp on 2009-04-27
> **shuukazedojo said:**
> Thanks for the reply. Thankfully, I didn't need to do any of that. My HD was full and was creating some new and interesting issues. I reduced the load and PRESTO! 

I DO think that a function like Winbloze System Restore should be added, though. Like the wiki entry I posted before says, it encourages people to do more with their computer without fear of never being able to return safely.

Glad you got your problem fixed.

The best system restore strategy in my opinion:
- Regular automatic backups (try SBackup or Rsync/Grsync)
- /home on a separate partition or drive, and 
- appropriate use of sudo

Far more efficient than system restore and relatively easy to setup - once and then forget about it until you need it.

EDIT: Also note, SBackup keeps a list of all of the applications that were installed as at any backup date and this allows you to easily restore the applications you require to get back to a particular point, as well as your data.

---

