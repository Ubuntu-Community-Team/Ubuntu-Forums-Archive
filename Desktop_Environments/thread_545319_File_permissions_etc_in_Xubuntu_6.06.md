---
title: "File permissions etc in Xubuntu 6.06"
date: 2007-09-07
forum: Desktop Environments
---

### Post by jamesr on 2007-09-07
Hi,

I have followed the excelcent instructions on howto Create a Separate home partition by Aysieu   at [www.pyschocats.net](www.pyschocats.net) but unfortunately I have a problem with deleting parts of the old directory.

The system is an archival server so there are several home directories in /home including a shared directory. I would like to delete various files from the /home_backup/shared using my main account on the rather than log-in as the other users and individually delete. This facility, I would also like to use on the new /home directory.

> 

jdsci@Tubby:/home_backup/shared$
jdsci@Tubby:/home_backup/shared$ ll
total 22336
drwxr-xr-x 12 nobody   nogroup     4096 2006-11-07 09:50 19XXJDSc.fol
drwxr-xr-x 23 nobody   nogroup     4096 2006-11-07 09:51 2000JDSc.fol
drwxr-xr-x 27 nobody   nogroup     4096 2006-11-07 09:51 2001JDSc.fol
drwxr-xr-x 27 nobody   nogroup     4096 2006-11-07 09:53 2002JDSc.fol
-rwxr--r--  1 jdoffice users      17114 2006-12-11 20:24 250.pdf
-rwxr--r--  1 jdoffice users      17114 2006-12-11 20:24 261.pdf
-rwxr--r--  1 jdoffice users      10535 2007-01-31 15:24 30_queens.pdf
-rwxr--r--  1 nobody   nogroup   475934 2006-11-12 09:27 6212-A2-GZ10-00.pdf
-rwxr--r--  1 nobody   nogroup   181082 2006-11-12 09:27 6381-A2-ZZ13-10.pdf
-rwxr--r--  1 nobody   nogroup   393819 2006-11-12 09:27 6381.pdf
-rwxr--r--  1 nobody   nogroup   125972 2006-11-12 09:27 Add_email_account_Outlook6.pdf
drwxr-xr-x  2 deskp450 users       4096 2007-06-14 10:57 Alpha
drwxr-xr-x  2 deskp450 users       4096 2007-06-14 10:57 Apache
drwxr-xr-x  6 deskp450 deskp450    4096 2007-05-28 07:45 Archive
-rwxr--r--  1 nobody   nogroup   241806 2006-11-12 09:27 changing_password_email_selfcare.pdf
drwxr-xr-x  3 deskp450 users       4096 2007-05-28 07:44 Compaq
-rwxr--r--  1 nobody   nogroup   257726 2006-11-12 09:27 Create_email.pdf
drwxr-xr-x  2 root     root        4096 2006-12-03 09:26 DCC
drwxr-xr-x  7 deskp450 users       4096 2007-06-14 11:00 DP450 Gene
-rwxr--r--  1 nobody   nogroup  3699534 2007-01-05 04:49 DVD_tools.zip
drwxr-xr-x  2 deskp450 users       4096 2007-06-14 10:55 Electronics
-rwxr--r--  1 nobody   nogroup    25052 2006-11-12 09:28 email_basics.pdf
lrwxrwxrwx  1 shared   shared        26 2006-09-20 15:53 Examples -> /usr/share/example-content
-rwxr--r--  1 nobody   nogroup    88272 2006-11-12 09:28 FTP_webspace.pdf
drwxr-xr-x  3 nobody   nogroup     4096 2006-11-07 09:56 Genealogy
drwxr-xr-x  2 deskp450 users       4096 2007-06-14 10:55 Hardware
drwxr-xr-x  3 archie   archie      4096 2007-01-15 04:32 Hiren_s_BootCD_8[1].4_by_soft-best.net
drwxr-xr-x  4 jdscil   jdscil      4096 2007-01-09 12:14 HPN5425
-rwxr--r--  1 nobody   nogroup    70906 2006-11-12 09:28 HSI_PUA_on_en.pdf
drwxr-xr-x 34 deskp450 deskp450    4096 2006-09-20 21:25 Laptop1
-rwxr--r--  1 deskp450 deskp450   23833 2006-09-05 22:24 mboximport-0.5.5.xpi
-rwxr--r--  1 deskp450 users      77956 2006-10-27 09:10 myaddresses.ldif
drwxr-xr-x  2 francis  francis     4096 2007-01-01 18:39 My Pictures
-rwxr--r--  1 deskp450 users      51828 2006-10-30 10:13 pag2001.TIF
-rwxr--r--  1 deskp450 users      51702 2006-10-30 10:13 pag2002.TIF
drwxr-xr-x  2 deskp450 users       4096 2006-11-01 21:43 Partition Magic 8.0
-rwxr--r--  1 nobody   nogroup   412605 2006-11-04 12:10 pia3_enu.chm
-rwxr--r--  1 nobody   nogroup  9773568 2006-11-04 12:10 piatrial_enu.exe
-rwxr--r--  1 jdoffice users      11548 2007-01-31 15:36 Queens07a1.pdf
drwxr-xr-x  2 deskp450 users       4096 2006-12-03 09:28 Standard setup
-rwxr--r--  1 deskp450 deskp450 1803864 2006-09-26 16:14 starjavapos_win32-linux-macosx_20050810.zip
-rwxr--r--  1 deskp450 deskp450     376 2006-10-13 22:48 Test1 DocA.rtf
-rwxr--r--  1 m41      m41          322 2006-10-13 21:16 Test1 Doc.rtf
-rwxr--r--  1 vgsci    vgsci    2950063 2006-10-03 17:53 tplitelx_complete.tar.tar
drwxr-xr-x  2 vgsci    vgsci       4096 2006-10-23 16:12 Treepad
drwxr-xr-x  2 archie   archie      4096 2007-03-01 20:12 UofWChTemp
drwxr-xr-x  3 deskp450 users       4096 2007-06-14 11:02 Utilites Viewers
-rwxr--r--  1 nobody   nogroup  1870104 2006-11-12 09:28 warm-refs.pdf
drwxr-xr-x  2 root     root        4096 2006-12-03 09:25 WMV
jdsci@Tubby:/home_backup/shared$


Yes I can use ```
sudo rm -rf /Laptop1
``` which works but if possible I would like to find a way using the GUI as well.

Best Wishes
Jim R

---

### Post by newlinux on 2007-09-07
I think using nautilus with root privileges would work.

```

gksudo nautilus

```

I think this would allow you to delete anything using nautilus, so be careful :)

---

### Post by newlinux on 2007-09-07
sorry, i just noted you are on Xubuntu, which uses xfce, so i don't know if it has nautilus or not. I suppose you could use thunar instead. I'm not as familiar with xubuntu.

---

### Post by niceguy123 on 2007-09-20
> **newlinux said:**
> sorry, i just noted you are on Xubuntu, which uses xfce, so i don't know if it has nautilus or not. I suppose you could use thunar instead. I'm not as familiar with xubuntu.

Thanks, you were right natutilus didn't work in xubuntu but thunar did. Thanks

---

