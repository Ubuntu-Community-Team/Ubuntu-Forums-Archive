---
title: "Setting up file server in Computer Lab."
date: 2009-05-16
forum: General Help
---

### Post by mreraw on 2009-05-16
Hi,  I would like to set up a Linux file/print server in my school's computer lab so that I don't have to assign seats or give flash drives to every student (these are elementary kids).  The problem is that I have little experience with Linux or any server for that matter.      

I read a few "How Tos" on setting up linux file servers, but there's still some things I'm unclear on...    

- We have 20 Leopard iMacs in the lab.  Would an old P4 with 512RAM and a 40gig HD be powerful enough to serve that many machines?  Later in the school year it will need to serve larger imovie and idvd projects.    

- I'm afraid something will go wrong and I won't be able to troubleshoot it immediately.  Is it possible to have the server synchronized or backing up daily to an external USB hard drive or flash drive?  That way, I always have the option of just transferring the files the "old fashion" way.    

Thanks in advance.

---

### Post by mb_webguy on 2009-05-17
> **mreraw said:**
> Hi,  I would like to set up a Linux file/print server in my school's computer lab so that I don't have to assign seats or give flash drives to every student (these are elementary kids).  The problem is that I have little experience with Linux or any server for that matter.
Have you considered using some sort of login to prevent students from accidentally or intentionally opening and modifying other students' work?  This would be fairly easy to do using Samba.
> **mreraw said:**
> I read a few "How Tos" on setting up linux file servers, but there's still some things I'm unclear on...    

- We have 20 Leopard iMacs in the lab.  Would an old P4 with 512RAM and a 40gig HD be powerful enough to serve that many machines?  Later in the school year it will need to serve larger imovie and idvd projects.
Yes to the first, probably to the second.  File and print servers don't do much by way of processing, so processor speed and memory aren't terribly important.  Make sure your swap file/partition is a decent size just in case.  Something in the range of 512MB to 1GB should be fine.

As for the storage... How many students do you have, and how large will the projects be?  Multiply the fist by the second, and add 4GB for the OS, and that's the minimum amount of storage you'll need.
> **mreraw said:**
> - I'm afraid something will go wrong and I won't be able to troubleshoot it immediately.  Is it possible to have the server synchronized or backing up daily to an external USB hard drive or flash drive?  That way, I always have the option of just transferring the files the "old fashion" way.    

Thanks in advance.
Yes, absolutely.  Numerous backup utilities are available, but it would really be fairly easy just to write a small script to take care of it.  The script itself would be something along the lines of...```
#! /bin/sh
cp -R /path/to/project_directory/* /path/to/backup_directory/
```The backup directory can be any existing directory, including an external drive.  (Since you're talking about using an external drive, you'd probably want to check to make sure the backup directory exists -- i.e. that the external drive is mounted -- before using the copy command, but I'm trying to keep things as simple as possible.)  You can then use anacron to schedule the script to be run every so many days.

Suppose you named the above script "backup_projects" and saved it to "/usr/local/bin".  (The easy way to do this would be to create it there in the first place by using the command "sudo nano /usr/local/bin/backup_projects" to open the file using nano and save it to that location when you exit.)  You would need to make the script executable with the command "sudo chmod +x /usr/local/bin/backup_projects".  Then you would schedule the script using anacron by putting it in the /etc/anacrontab file.  You would open the file using the command "sudo nano /etc/anacrontab", and you would add an entry to the end of the file along the lines of the following...```
*days*   20   *some_name_for_the_job*   /usr/local/bin/backup_projects
```... where *days* is the number of days between backups, 20 is the period of time in minutes anacron should wait before doing the backup when it notices that one needs to be done, and *some_name_for_the_job* is any name you want to give the job (which can't contain spaces or slashes, but can otherwise be whatever you want).  I used 20 for the delay, because you'll notice when you open the /etc/anacrontab file that there are already some jobs listed, and you want to give them time to finish before you start the backup.  The name for the job is just something anacron will use to identify the job in log entries and other such messages.

One thing to keep in mind is that you can't specify the exact time the backup will be performed using anacron, only the interval between updates in days.  This usually doesn't matter, but it does mean you should be careful if you decide to use an external drive for backups to make sure that you're not in the middle of a backup when you go to remove the drive.  Since you should be properly unmounting the drive before yanking it out of the machine, and I don't think it will let you unmount a drive while data is being written to it, this shouldn't be much of a problem.

If the exact time the backup is performed is an issue, there are other methods available for scheduling the backup.  I just used anacron because it's fairly straightforward -- just add a relatively simple entry to a text file -- and seemed appropriate for what you want to do.

---

### Post by mb_webguy on 2009-05-17
> **mreraw said:**
> Hi,  I would like to set up a Linux file/print server in my school's computer lab so that I don't have to assign seats or give flash drives to every student (these are elementary kids).  The problem is that I have little experience with Linux or any server for that matter.
Have you considered using some sort of login to prevent students from accidentally or intentionally opening and modifying other students' work?  This would be fairly easy to do using Samba.
> **mreraw said:**
> I read a few "How Tos" on setting up linux file servers, but there's still some things I'm unclear on...    

- We have 20 Leopard iMacs in the lab.  Would an old P4 with 512RAM and a 40gig HD be powerful enough to serve that many machines?  Later in the school year it will need to serve larger imovie and idvd projects.
Yes to the first, probably to the second.  File and print servers don't do much by way of processing, so processor speed and memory aren't terribly important.  Make sure your swap file/partition is a decent size just in case.  Something in the range of 512MB to 1GB should be fine.

As for the storage... How many students do you have, and how large will the projects be?  Multiply the fist by the second, add 4GB for OS, and that's the minimum amount of storage you'll need.
> **mreraw said:**
> - I'm afraid something will go wrong and I won't be able to troubleshoot it immediately.  Is it possible to have the server synchronized or backing up daily to an external USB hard drive or flash drive?  That way, I always have the option of just transferring the files the "old fashion" way.    

Thanks in advance.
Yes, absolutely.  Numerous backup utilities are available, but it would really be fairly easy just to write a small script to take care of it.  The script itself would be something along the lines of...```
#! /bin/sh
cp -R /path/to/project_directory/* /path/to/backup_directory/
```The backup directory can be any existing directory, including an external drive.  (Since you're talking about using an external drive, you'd probably want to check to make sure the backup directory exists -- i.e. that the external drive is mounted -- before using the copy command, but I'm trying to keep things as simple as possible.)  You can then use anacron to schedule the script to be run every so many days.

Suppose you named the above script "backup_projects" and saved it to "/usr/local/bin".  (The easy way to do this would be to create it there in the first place by using the command "sudo nano /usr/local/bin/backup_projects" to open the file using nano and save it to that location when you exit.)  You would need to make the script executable with the command "sudo chmod +x /usr/local/bin/backup_projects".  Then you would schedule the script using anacron by putting it in the /etc/anacrontab file.  You would open the file using the command "sudo nano /etc/anacrontab", and you would add an entry to the end of the file along the lines of the following...```
*days*   20   *some_name_for_the_job*   /usr/local/bin/backup_projects
```... where *days* is the number of days between backups, 20 is the period of time in minutes anacron should wait before doing the backup when it notices that one needs to be done, and *some_name_for_the_job* is any name you want to give the job (which can't contain spaces or slashes, but can otherwise be whatever you want).  I used 20 for the delay, because you'll notice when you open the /etc/anacrontab file that there are already some jobs listed, and you want to give them time to finish before you start the backup.  The name for the job is just something anacron will use to identify the job in log entries and other such messages.

One thing to keep in mind is that you can't specify the exact time the backup will be performed using anacron, only the interval between updates in days.  This usually doesn't matter, but it does mean you should be careful if you decide to use an external drive for backups to make sure that you're not in the middle of a backup when you go to remove the drive.  Since you should be properly unmounting the drive before yanking it out of the machine, and I don't think it will let you unmount a drive while data is being written to it, this shouldn't be much of a problem.

If the exact time the backup is performed is an issue, there are other methods available for scheduling the backup.  I just used anacron because it's fairly straightforward -- just add a relatively simple entry to a text file -- and seemed appropriate for what you want to do.

---

### Post by mb_webguy on 2009-05-17
> **mreraw said:**
> Hi,  I would like to set up a Linux file/print server in my school's computer lab so that I don't have to assign seats or give flash drives to every student (these are elementary kids).  The problem is that I have little experience with Linux or any server for that matter.
Have you considered using some sort of login to prevent students from accidentally or intentionally opening and modifying other students' work?  This would be fairly easy to do using Samba.
> **mreraw said:**
> I read a few "How Tos" on setting up linux file servers, but there's still some things I'm unclear on...    

- We have 20 Leopard iMacs in the lab.  Would an old P4 with 512RAM and a 40gig HD be powerful enough to serve that many machines?  Later in the school year it will need to serve larger imovie and idvd projects.
Yes to the first, probably to the second.  File and print servers don't do much by way of processing, so processor speed and memory aren't terribly important.  Make sure your swap file/partition is a decent size just in case.  Something in the range of 512MB to 1GB should be fine.

As for the storage... How many students do you have, and how large will the projects be?  Multiply the first by the second, add 4GB for OS, and that's the minimum amount of storage you'll need.
> **mreraw said:**
> - I'm afraid something will go wrong and I won't be able to troubleshoot it immediately.  Is it possible to have the server synchronized or backing up daily to an external USB hard drive or flash drive?  That way, I always have the option of just transferring the files the "old fashion" way.    

Thanks in advance.
Yes, absolutely.  Numerous backup utilities are available, but it would really be fairly easy just to write a small script to take care of it.  The script itself would be something along the lines of...```
#! /bin/sh
cp -R /path/to/project_directory/* /path/to/backup_directory/
```The backup directory can be any existing directory, including an external drive.  (Since you're talking about using an external drive, you'd probably want to check to make sure the backup directory exists -- i.e. that the external drive is mounted -- before using the copy command, but I'm trying to keep things as simple as possible.)  You can then use anacron to schedule the script to be run every so many days.

Suppose you named the above script "backup_projects" and saved it to "/usr/local/bin".  (The easy way to do this would be to create it there in the first place by using the command "sudo nano /usr/local/bin/backup_projects" to open the file using nano and save it to that location when you exit.)  You would need to make the script executable with the command "sudo chmod +x /usr/local/bin/backup_projects".  Then you would schedule the script using anacron by putting it in the /etc/anacrontab file.  You would open the file using the command "sudo nano /etc/anacrontab", and you would add an entry to the end of the file along the lines of the following...```
*days*   20   *some_name_for_the_job*   /usr/local/bin/backup_projects
```... where *days* is the number of days between backups, 20 is the period of time in minutes anacron should wait before doing the backup when it notices that one needs to be done, and *some_name_for_the_job* is any name you want to give the job (which can't contain spaces or slashes, but can otherwise be whatever you want).  I used 20 for the delay, because you'll notice when you open the /etc/anacrontab file that there are already some jobs listed, and you want to give them time to finish before you start the backup.  The name for the job is just something anacron will use to identify the job in log entries and other such messages.

One thing to keep in mind is that you can't specify the exact time the backup will be performed using anacron, only the interval between backups in days.  This usually doesn't matter, but it does mean you should be careful if you decide to use an external drive for backups to make sure that you're not in the middle of a backup when you go to remove the drive.  Since you should be properly unmounting the drive before yanking it out of the machine, and I don't think it will let you unmount a drive while data is being written to it, this shouldn't be much of a problem.

If the exact time the backup is performed is an issue, there are other methods available for scheduling the backup.  I just used anacron because it's fairly straightforward -- just add a relatively simple entry to a text file -- and seemed appropriate for what you want to do.

---

### Post by mb_webguy on 2009-05-17
What the frak?  Three duplicate posts???  I know I only hit the button once...

---

### Post by mreraw on 2009-05-18
> **mb_webguy said:**
> Have you considered using some sort of login to prevent students from accidentally or intentionally opening and modifying other students' work?  This would be fairly easy to do using Samba.

Yes to the first, probably to the second.  File and print servers don't do much by way of processing, so processor speed and memory aren't terribly important.  Make sure your swap file/partition is a decent size just in case.  Something in the range of 512MB to 1GB should be fine.

As for the storage... How many students do you have, and how large will the projects be?  Multiply the fist by the second, and add 4GB for the OS, and that's the minimum amount of storage you'll need.

Yes, absolutely.  Numerous backup utilities are available, but it would really be fairly easy just to write a small script to take care of it.  The script itself would be something along the lines of...```
#! /bin/sh
cp -R /path/to/project_directory/* /path/to/backup_directory/
```The backup directory can be any existing directory, including an external drive.  (Since you're talking about using an external drive, you'd probably want to check to make sure the backup directory exists -- i.e. that the external drive is mounted -- before using the copy command, but I'm trying to keep things as simple as possible.)  You can then use anacron to schedule the script to be run every so many days.

Suppose you named the above script "backup_projects" and saved it to "/usr/local/bin".  (The easy way to do this would be to create it there in the first place by using the command "sudo nano /usr/local/bin/backup_projects" to open the file using nano and save it to that location when you exit.)  You would need to make the script executable with the command "sudo chmod +x /usr/local/bin/backup_projects".  Then you would schedule the script using anacron by putting it in the /etc/anacrontab file.  You would open the file using the command "sudo nano /etc/anacrontab", and you would add an entry to the end of the file along the lines of the following...```
*days*   20   *some_name_for_the_job*   /usr/local/bin/backup_projects
```... where *days* is the number of days between backups, 20 is the period of time in minutes anacron should wait before doing the backup when it notices that one needs to be done, and *some_name_for_the_job* is any name you want to give the job (which can't contain spaces or slashes, but can otherwise be whatever you want).  I used 20 for the delay, because you'll notice when you open the /etc/anacrontab file that there are already some jobs listed, and you want to give them time to finish before you start the backup.  The name for the job is just something anacron will use to identify the job in log entries and other such messages.

One thing to keep in mind is that you can't specify the exact time the backup will be performed using anacron, only the interval between updates in days.  This usually doesn't matter, but it does mean you should be careful if you decide to use an external drive for backups to make sure that you're not in the middle of a backup when you go to remove the drive.  Since you should be properly unmounting the drive before yanking it out of the machine, and I don't think it will let you unmount a drive while data is being written to it, this shouldn't be much of a problem.

If the exact time the backup is performed is an issue, there are other methods available for scheduling the backup.  I just used anacron because it's fairly straightforward -- just add a relatively simple entry to a text file -- and seemed appropriate for what you want to do.


Thanks webguy, looks like a of great information!  I'm actually looking forward to getting to work tomorrow so I can try this.  

I have considered login options for protecting the student files.  I think I want to start off simple and just create a single login for each classroom. If this goes well, I'd like to make the server available schoolwide and then I'd give each a unique log in.

---

