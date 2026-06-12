---
title: "File locks and users can't save"
date: 2009-04-16
forum: General Help
---

### Post by Hopelesslylost on 2009-04-16
Hi, I have been trawling through the forums but have as yet not found an answer.

We currently have 3 Admins working on a shared Excel Workbook, the problem (that some may be able to see straight away) is that when one Admin saves, the file gets locked to them and the others can't save the file.

I have created the user accounts as Admins (in the User and Groups section in Ubuntu) and added them to a group that has full admin rights.

I created the Samba share and added them all as users able to view and write to the files.

So far the only way around this is to go to the directory in Terminal and type;

sudo chmod 777 *Excel Workbook Name* 

This then removes the lock and others can save.

The Admins are using this as an excuse not to get any work done, really need some help and any you could provide would be greatly appeciated.

Thanks.

---

### Post by Hopelesslylost on 2009-04-16
Just for some additional information, all of the other office PC's have Windows XP Pro installed.

Our previous Windows XP server was fine and didn't have these issues.

I understand that I may be missing something really simple so any help would be really appreciated.


Thanks.

---

### Post by Hopelesslylost on 2009-04-16
Ok, I'm not sure if people just dont know how to do this or if it is even possible.

So, is there a way to create a batch file on the Windows XP machines that would sent the command to Ubuntu to unlock the file?

The same command I'm using at the minute;

sudo chmod 777 *Excel Workbook Name*

Is this a possibility?

---

