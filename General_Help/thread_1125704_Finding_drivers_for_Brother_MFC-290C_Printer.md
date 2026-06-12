---
title: "Finding drivers for Brother MFC-290C Printer?"
date: 2009-04-14
forum: General Help
---

### Post by Redundant Username on 2009-04-14
After I find them, how do I install them?

---

### Post by Cheesehead on 2009-04-14
You find them, with the instructions at [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

---

### Post by Redundant Username on 2009-04-15
There are no drivers for that printer.

---

### Post by plucky on 2009-04-16
> **Redundant Username said:**
> There are no drivers for that printer.

Are you sure? Check again! See this [link](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-290C)

Good Luck

---

### Post by Redundant Username on 2009-04-16
Thanks.

---

### Post by Redundant Username on 2009-04-16
I need 64-bit drivers.:cry:
Could someone write and compile 64-bit drivers? The source code is available for download.

---

### Post by Redundant Username on 2009-04-16
*shameless self bump*

---

### Post by Thinkin on 2010-02-15
Download the source code from here:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_src.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_src.html")

Extract the file and find the subdirectory for the MFC290.  Extract the contents to a directory of your choice.

Go to the SCRIPTS subdirectory of the extracted file/folders.  Right click on the file labeled "cupswrappermfc290c", go to Properties, Permissions tab and make it executable.

Use Applications>Accessories>Terminal and then navigate to the downloaded directory where SCRIPT is located.  Now type the following:

sudo ./cupswrappermfc290c

Enter your password when prompted and the printer should show up in your list of printers.  From there you just need to right-click, Properties and change the device URL to either USB or SMB if it is shared on a Windows workgroup.

---

### Post by parsh78 on 2010-02-18
Thanks for the info on building printer driver. it really helped.

---

### Post by point_communication on 2010-02-26
> **Redundant Username said:**
> Thanks.
can u send me link of mfc -290c priter

---

### Post by Feenix3k on 2010-03-06
> **Thinkin said:**
> Download the source code from here:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_src.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_src.html")

Extract the file and find the subdirectory for the MFC290.  Extract the contents to a directory of your choice.

Go to the SCRIPTS subdirectory of the extracted file/folders.  Right click on the file labeled "cupswrappermfc290c", go to Properties, Permissions tab and make it executable.

Use Applications>Accessories>Terminal and then navigate to the downloaded directory where SCRIPT is located.  Now type the following:

sudo ./cupswrappermfc290c

Enter your password when prompted and the printer should show up in your list of printers.  From there you just need to right-click, Properties and change the device URL to either USB or SMB if it is shared on a Windows workgroup.

After I did the above I got the following:

ERROR : Brother LPD filter is not installed.
chmod: cannot access `/usr/local/Brother/Printer/mfc290c/inf/brmfc290crc': No such file or directory
chmod: cannot access `/usr/local/Brother/Printer/mfc290c/inf': No such file or directory
 * Restarting Common Unix Printing System: cupsd

---

