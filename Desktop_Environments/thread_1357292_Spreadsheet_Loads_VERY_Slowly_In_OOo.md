---
title: "Spreadsheet Loads VERY Slowly In OOo"
date: 2009-12-17
forum: Desktop Environments
---

### Post by rykel on 2009-12-17
Hi,

I have a Microsoft Excel file which opens up very quickly in Microsoft Office. (less than 15 secs)

However, the same file takes 3 minutes or so to load up in OpenOffice.org with some warning about macros being disabled. The bulk of the startup time was some "calculating..." done by OpenOffice.org.

I have saved the file as an .ods with the good news result that the filesize went down from 20mb to 500kb, but the problem still persists!

Could you please advise?

Thank you!!

---

### Post by earthpigg on 2009-12-17
OOo needs to spend a crap ton of time converting it to standard formats, because microsoft does not adhere to standard formats and hides how their formats work.

so the efficient method that allows the secret format to open in 15 seconds is a itself a secret. it needs to be 'decoded' every time you open it.

try this: open it, save it in a native open standard format (OOo default), and try opening it again?

---

### Post by rykel on 2009-12-17
Hi pigg   :)

Indeed I have converted the .xls file into .ods using both OpenOffice.org and Gnumeric... and guess what, the resulting .ods files themselves take ages to open up using OpenOffice.org and Gnumeric.

Please help??

---

### Post by kerry_s on 2009-12-17
when is ooo not slow? :lolflag:
(just joking, it's fast enough for what it does)

have you done the usual tweaks? (up the memory use, disable java)

---

### Post by rykel on 2009-12-17
> **kerry_s said:**
> when is ooo not slow? :lolflag:
(just joking, it's fast enough for what it does)

have you done the usual tweaks? (up the memory use, disable java)

Hi Kerry,

No, I assumed that the default is already optimized... I have just disabled the Java Runtime Environment... but HOW do I "up" the memory... and by how much??

p/s. The office where I helped to set up Ubuntu is getting horrified at the amount of time it takes for their spreadsheet to start up, and are suggesting that if it is so troublesome, then might as well just stick to Microsoft Office... Time is running out for my Ubuntu evangelism effort, so please help!!

---

### Post by kerry_s on 2009-12-17
tools-> options-> memory

i always do 128mb & 32mb.

i'm on windows right now but the office should be the same, pic:

---

### Post by rykel on 2009-12-18
Hi,

I tried your suggestions, and indeed there was a marked improvement... HOWEVER, it still took OpenOffice.org at least 2-3 minutes to open the file that takes Microsoft Office only a second to load.

:(

---

### Post by kerry_s on 2009-12-18
> **rykel said:**
> Hi,

I tried your suggestions, and indeed there was a marked improvement... HOWEVER, it still took OpenOffice.org at least 2-3 minutes to open the file that takes Microsoft Office only a second to load.

:(

that's strange, try starting "soffice" from terminal then use the file open to open the file see what kind of output it's giving in the terminal.

if you could attach a sample of the file, we might better understand what your talking about.

---

### Post by Dennis N on 2009-12-18
You might also try Gnumeric and see if it meets your needs. I found it quicker than Open Ofice spreadsheet and it had all the features I needed. It imports Excel files as well.

---

