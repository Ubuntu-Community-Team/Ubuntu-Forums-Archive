---
title: "evolution data restore problem"
date: 2011-06-11
forum: Desktop Environments
---

### Post by raunhar on 2011-06-11
I was using 11.04 till yesterday, but as my laser printer and the bluetooth were not working in this version, i switched back to 10.10

I had taken the backup of evolution through backup settings.
But when I tried to restore the mail settings, it did not recognise the file.

Error that shows up is:
Invalid Evolution back up file.
Please select a valid backup file to restore.

The file that is being selected is: evolution-backup.tar.gz

What should be done for the restore now.

pl. suggest.

---

### Post by Pengwyn44 on 2011-06-21
I have had a similar problem. When I go to File - Backup settings I get an error message saying that it is an invalid operation. After shutting the error message box, the backup can then be effected!

You could also try finding the backup file in the File Manager, right click and choose "Open with other application", then select Evolution.

Pengwyn44

---

### Post by MarjaE on 2011-10-20
> **Pengwyn44 said:**
> I have had a similar problem. When I go to File - Backup settings I get an error message saying that it is an invalid operation. After shutting the error message box, the backup can then be effected!

You could also try finding the backup file in the File Manager, right click and choose "Open with other application", then select Evolution.

Pengwyn44

Neither workaround works for me.

---

### Post by Pengwyn44 on 2011-10-21
I have tried to replicate your problem as I have two computers, one running 11.04 and one running 10.10. The answer is that your backup file can only be opened by 11.04. Once opened, I cannot find any way of reading the database files which appear to be written in binary.
The files are located in /home/yourname/.local/share/evolution

You can, of course, when the files are open in 11.04, print the information to paper and then keyboard it back in when you are in 10.10.

The better solution is to make 11.04 work for you.

Pengwyn44

---

