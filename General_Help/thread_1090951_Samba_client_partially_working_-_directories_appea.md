---
title: "Samba client partially working - directories appear, but can't see file contents"
date: 2009-03-08
forum: General Help
---

### Post by Greg Davis on 2009-03-08
I am trying to read files on a windows share from my Ubuntu server 8.10 machine.  I see the directory and the files in the share, but can not display the contents using the "cat" command.  

I installed the Samba client with "sudo apt-get install smbfs smbclient".  Then made a directory for the mount point using "mkdir /mnt/storage".  I mounted share using "sudo smbmount //192.168.1.10/data /mnt/storage".  I changed the directory using "cd /mnt/storage".  The directories displayed using "ls" command as shown below.  I changed the directory using "cd development" and then "cd sql" followed by another "ls" to see the files.  Now when I do the "cat customer.txt" command, I get the message "No such file or directory".  I copied my results below in case it helps.

greg@dbsrv:/mnt/storage/development$ ls
Apache Tomcat Web Application Server  MySQL   sql         Sun JDK  Winscp
Apache Web Server                     PuTTY   Subclipse   Ubuntu
Eclipse - Ganymede SDK                Spring  Subversion  VNC
greg@dbsrv:/mnt/storage/development$ cd sql
greg@dbsrv:/mnt/storage/development/sql$ ls
customer_1.sql  customer_2.txt  customer_3.qbquery  test.txt
greg@dbsrv:/mnt/storage/development/sql$ cat test.txt
cat: test.txt: No such file or directory
greg@dbsrv:/mnt/storage/development/sql$

Not sure where to go from here.  I thought I was home free once I could see the share and the directories, but that was not the case.  If you could point me in the right direction, that would be great.  Thanks!

---

### Post by dcstar on 2009-03-08
> **Greg Davis said:**
> I am trying to read files on a windows share from my Ubuntu server 8.10 machine.  I see the directory and the files in the share, but can not display the contents using the "cat" command.  

I installed the Samba client with "sudo apt-get install smbfs smbclient".  Then made a directory for the mount point using "mkdir /mnt/storage".  I mounted share using "sudo smbmount //192.168.1.10/data /mnt/storage".  I changed the directory using "cd /mnt/storage".  The directories displayed using "ls" command as shown below.  I changed the directory using "cd development" and then "cd sql" followed by another "ls" to see the files.  Now when I do the "cat customer.txt" command, I get the message "No such file or directory".  I copied my results below in case it helps.

greg@dbsrv:/mnt/storage/development$ ls
Apache Tomcat Web Application Server  MySQL   sql         Sun JDK  Winscp
Apache Web Server                     PuTTY   Subclipse   Ubuntu
Eclipse - Ganymede SDK                Spring  Subversion  VNC
greg@dbsrv:/mnt/storage/development$ cd sql
greg@dbsrv:/mnt/storage/development/sql$ ls
customer_1.sql  customer_2.txt  customer_3.qbquery  test.txt
greg@dbsrv:/mnt/storage/development/sql$ cat test.txt
cat: test.txt: No such file or directory
greg@dbsrv:/mnt/storage/development/sql$

Not sure where to go from here.  I thought I was home free once I could see the share and the directories, but that was not the case.  If you could point me in the right direction, that would be great.  Thanks!

use ```
ls -al
``` to see actual file permissions.

---

### Post by Greg Davis on 2009-03-09
I do not think it is an authority issue.  I listed the directory and files access permissions below.  The file names show up in light green as though they are not native Linux files.  Could this have something to do with it?

greg@dbsrv:/mnt/storage/development/sql$ ls -ld
drwxrwxrwx 2 35000 42000 0 2009-03-08 20:50 .
greg@dbsrv:/mnt/storage/development/sql$ ls -al
total 5120
drwxrwxrwx  2 35000 42000   0 2009-03-08 20:50 .
drwxrwxrwx 15 35000 42000   0 2009-03-08 20:29 ..
-rwxrw-rw-  1 35000 42000   0 2009-03-08 20:29 [COLOR="Lime"]customer_1.sql[/COLOR]
-rwxrw-rw-  1 35000 42000 579 2009-03-08 20:42 [COLOR="Lime"]customer_2.txt[/COLOR]
-rwxrw-rw-  1 35000 42000 582 2009-02-16 22:01 [COLOR="Lime"]customer_3.qbquery[/COLOR]
-rwxrw-rw-  1 35000 42000  20 2009-03-08 20:50 [COLOR="Lime"]test.txt[/COLOR]
greg@dbsrv:/mnt/storage/development/sql$ cat test.txt
cat: test.txt: No such file or directory
greg@dbsrv:/mnt/storage/development/sql$

---

### Post by dcstar on 2009-03-11
> **Greg Davis said:**
> I do not think it is an authority issue.  I listed the directory and files access permissions below.  The file names show up in light green as though they are not native Linux files.  Could this have something to do with it?

greg@dbsrv:/mnt/storage/development/sql$ ls -ld
drwxrwxrwx 2 35000 42000 0 2009-03-08 20:50 .
greg@dbsrv:/mnt/storage/development/sql$ ls -al
total 5120
drwxrwxrwx  2 35000 42000   0 2009-03-08 20:50 .
drwxrwxrwx 15 35000 42000   0 2009-03-08 20:29 ..
-rwxrw-rw-  1 35000 42000   0 2009-03-08 20:29 [COLOR="Lime"]customer_1.sql[/COLOR]
-rwxrw-rw-  1 35000 42000 579 2009-03-08 20:42 [COLOR="Lime"]customer_2.txt[/COLOR]
-rwxrw-rw-  1 35000 42000 582 2009-02-16 22:01 [COLOR="Lime"]customer_3.qbquery[/COLOR]
-rwxrw-rw-  1 35000 42000  20 2009-03-08 20:50 [COLOR="Lime"]test.txt[/COLOR]
greg@dbsrv:/mnt/storage/development/sql$ cat test.txt
cat: test.txt: No such file or directory
greg@dbsrv:/mnt/storage/development/sql$

What you see is not always what is there, try:

```
ls -b
cat *.txt
```

I suspect you have a codepage/rights issue with mounting that particular share, or you may want to read this:

[http://ubuntuforums.org/showthread.php?t=255872](http://ubuntuforums.org/showthread.php?t=255872)

Please keep in mind that with any shared resource there are two sets of security: The "Share" level and then the actual item level security of the resource you are accessing. If either level of security blocks a particular type of access, then things won't happen.

For instance, the "Guest" Windows account may allow you to read/transverse the directory (so you see the file names) but not allow you to read any actual file.

---

### Post by Greg Davis on 2009-03-12
It now works.  I had a case sensitive issue on one of the directory names.  I typed in "development" as the name of the directory, and while it found everything and listed the files just fine using "ls -l" it did not work with "cat".  I tried using "Development" with a capital "D" like it is in windows and it worked.

In addition, I changed the permissions on the directories by right clicking on the folder in Windows Vista and gave full access to Everyone.  While this is not secure and I will scale it down, I just wanted to see it working.

David, thanks for pointing me in the right direction!

greg@dbsrv:~$ sudo smbmount //192.168.1.10/data /mnt/storage
Password:
greg@dbsrv:~$ cd /mnt/storage
greg@dbsrv:/mnt/storage$ cd Development
greg@dbsrv:/mnt/storage/Development$ ls
Apache Tomcat Web Application Server OneDeep.txt  sql
greg@dbsrv:/mnt/storage/Development$ cat OneDeep.txt
Onedeep contains this stuff...

---

