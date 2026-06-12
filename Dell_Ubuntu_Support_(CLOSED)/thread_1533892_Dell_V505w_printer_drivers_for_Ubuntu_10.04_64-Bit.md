---
title: "Dell V505w printer drivers for Ubuntu 10.04 64-Bit"
date: 2010-07-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by poordamnedfool on 2010-07-18
Cannot seem to find any information on drivers for the Dell V505w printer for Ubuntu 10.04 64-Bit. Is there a work around out there if there are no drivers?

Thanks

---

### Post by poordamnedfool on 2010-07-25
No one else has experienced this problem?

---

### Post by Ozymandias97 on 2010-09-13
Yes I have the problem - Dell only supports 8.04 distro for V505 I think

Don't know if anyone has written open-source version?

---

### Post by anotherdike on 2010-09-24
I will be testing the Dell v505w under 10.04x64 within the next few days.  I will report back with what I find.  Or not.

EDIT:  Have tested the V505w under 64bit 10.04, it did not work.  Installed 32bit 10.04 and tried again, it worked using the 8.04 driver available at [http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R201206&SystemID=PRN_INKJET_V505&servicetag=&os=UB80&osl=en&deviceid=16451&devlib=0&typecnt=0&vercnt=2&catid=-1&impid=-1&formatcnt=0&libid=40&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=279374](http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R201206&SystemID=PRN_INKJET_V505&servicetag=&os=UB80&osl=en&deviceid=16451&devlib=0&typecnt=0&vercnt=2&catid=-1&impid=-1&formatcnt=0&libid=40&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=279374).

Note that I followed the printer addition via CUPS as outlined in the readme.  The printer takes about 15 seconds to start printing after the job has been sent.

---

### Post by oldtime on 2010-11-22
Any news on this front? I upgraded from 8.04 to 10.04 a week ago, and this is the only bug I've been trying to sleuth out.

When I tried to print from OpenOffice or print a test page, I got the following error:
#Print Error #There was a problem processing document 'Test Page' (job 180)
 

 Diagnosing the error, I found under “Job attributes”
 #/usr/local/dell/dldw/bin/printdriver failed
 

I reinstalled the driver from [http://support.dell.com/support/down...&fileid=279374]("http://support.dell.com/support/down...&fileid=279374.") and got the same error.

From the readme.txt file, I followed the CUPS 1.4.3 prompts to try and add the printer, I got the same 
error message as before:
*"/usr/local/dell/dldw/bin/printdriver failed"*

Anyone have any luck with this?

---

### Post by poordamnedfool on 2011-01-26
In the end I ended up running Ubuntu 32 bit with the PAE kernel, much better choice for me anyways.

---

