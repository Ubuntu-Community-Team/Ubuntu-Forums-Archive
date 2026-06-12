---
title: "Canon network printer stays at 'processing'"
date: 2009-01-05
forum: General Help
---

### Post by SRTS on 2009-01-05
Canon LBP-5050n (colour laser) is connected to the LAN. It seems to have been added flawlessly in CUPS web interface, at least I didn't get any error message. It gets recognized as "Canon_LBP5050_1.01_<ip>".

However, when I click 'Print Test Page', the job list shows that job at 'processing since..' but it isn't printed, it'll just stay at 'processing' until I cancel it.

From the CUPS driver list with '(recommended)' drivers, I tried
-Canon LBP-5360 Foomatic/cljet5
-Canon LBP-1000 - CUPS+Gutenprint v5.2.0-rc1
-Canon LBP-1000 Foomatic/ljet4
-Canon LBP-4+ Foomatic/lbp8

Any ideas?

(it says "Printer is now on-line." behind the printer name, and also"Printer State: idle, accepting jobs, published.", so seems it should work to me?)

---

### Post by SRTS on 2009-01-06
Doesn't anyone know how to make this Canon printer work? Do I need to install any extra packages? I installed foomatic and gutenprint. I didn't find any 'capt' packages though.

---

### Post by SRTS on 2009-01-06
On Canon's page I found after some search the 2 files
cndrvcups-capt_1.80-1_i386.deb
cndrvcups-common_1.80-1_i386.deb
installed them, now I can choose between 4 entries which all go
'Canon LBP5000 CAPT ver.1.3'
but still the printer just wouldn't show any sign of receiving a job, and cups tell me "processing" forever.

I also tried those 2 files in a 1.60 version, didn't change anything though.

Help, please. It must be possible to make a network printer work somehow :/

---

### Post by SRTS on 2009-01-06
After deinstalling the two deb files, I tried to delete and re-add the printer in CUPS, however, suddenly the 'find printer' function shows no printers!
Time to look which other linux distribution is able to handle a big-brand printer I guess.

---

### Post by cweinhofer on 2011-07-28
I hope that there has been a solution found for this between when this guy posted and now. I am a newbie running Ubuntu 11.04 (which has been very good otherwise) trying to install another LBP50XX series printer and have basically the same issue.

Following Ubuntu's [instructions for the CAPT driver]("https://help.ubuntu.com/community/CanonCaptDrv190"), the printer installed very easily. However, it won't print anything. I have tried LibreWriter, a text document, a test page, and a network job from windows. They all sit at "Processing" indefinitely (the longest I waited was 3 hrs).

If anyone knows of a solution, it would be appreciated.

---

### Post by Wayne_V on 2011-07-28
I don't know about your Canon, but mine (MP990) would not work with the opensource drivers.   It works fine with turboprint tho.   Check the documentation there ([http://www.turboprint.info/](http://www.turboprint.info/)) and see if yours is listed.  You can download a 30day trial driver to see if it works for you.

---

### Post by Wayne_V on 2011-07-28
a quick look doesn't show your printer as supported by turboprint but canon does have a CUPS driver for it:  [http://software.canon-europe.com/products/0010663.asp](http://software.canon-europe.com/products/0010663.asp)

---

### Post by cweinhofer on 2011-07-28
Wayne_V, thanks for your quick reply. Not too big of a disappointment about turboprint. Looks like it would be helpful, but having to pay for it defeats some of the purpose of using Linux.

I did download the drivers from the canon website, unpacked, and "installed" them. The Ubuntu Software Center told me that they were already installed - presumably from the PPA on the Ubuntu help page.

Anyway, tied a few other methods since the post a few hours ago and still no joy.

---

