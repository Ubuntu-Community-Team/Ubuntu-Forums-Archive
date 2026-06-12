---
title: "Printer only uses ones digit for # of copies"
date: 2009-02-16
forum: General Help
---

### Post by elusivespoon on 2009-02-16
I had a big print job to do, so I hooked up the office printer to my Linux laptop. But when trying to print multiple copies, only the ones digit of the copies number would be used, ignoring the tens digit and above. If that's confusing, here's a table for the number of copies selected, compared to those actually printed:
```
Selected  : Printed
1         : 1
2         : 2
     . . .
9         : 9
10        : 0
11        : 1
     . . .
19        : 9
     . . .
99        : 9
```

I first noticed this problem in Acrobat Reader, but then I opened up the printer properties for the printer, and under job options changed the number of copies to be printed by default and had the same problem.

Has anyone else had this problem? Is it a problem with the printer, the drivers, or the printing system Ubuntu uses? The printer is an HP Laserjet 2550L. The driver I am using was automatically downloaded by the Ubuntu 8.10 printing configuration.

I just did a quick test in Windows and it does not have the same problem. In fact, judging by how quickly the copies are printed with windows (one right after another), and how slowly with Linux (a long pause between each page), it seems the printer is not being sent the actual number of copies, but the job is resent once for each copy. The lesson here seems to be don't print long jobs in Linux, and don't use Linux only fonts in documents.

---

### Post by elusivespoon on 2009-03-12
*BUMP*
Can anyone try printing more than 9 copies and confirm whether or not this problem is unique to me/my printer.

---

### Post by Matsukaze on 2009-03-12
I have been able to duplicate this problem on one of my printers, but the other one works correctly. I printed a text file from the command line using the command  ```
lp -d Br2 -n2 test.txt
```Two copies printed. When I set n to 10, nothing was printed. With n set to 12, 2 copies printed. I looked in /var/log/cups/page_log and saw that the num-pages field was being set to the last digit of the number of pages called for on the command line, e.g. with -n12 in the lp command num-pages was 2, rather than 12. This was using my Brother HL-5170DN printer, which is a Postscript (actually Brother's clone of Postscript) capable printer.

When I print the file with my Canon iP6700D, the page_log file contains a separate line for each requested copy of the file, each with num-pages equal to 1.

It appears to me that this problem only occurs when the Linux printing system attempts to use the printer's own multiple-page printing, rather than just sending the print job to the printer multiple times. Unfortunately, I don't know enough about how Cups and its associated programs work to track the problem down any better.

---

