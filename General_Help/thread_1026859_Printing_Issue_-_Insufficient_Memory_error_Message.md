---
title: "Printing Issue - Insufficient Memory error Message"
date: 2008-12-31
forum: General Help
---

### Post by arepaking on 2008-12-31
Hello Experts,
I've been trying to print a PDF (Doc size is 1.9MB) but I am not getting good results.

Every time I try to print, a sheet come out of the printer with the following message:

```
PCL5e ERROR - Insufficient Memory!!!!
 VERSION: PCL5e 1.35 10-20-2000
```

Now, I have a P4 with 3GB RAM running Ubuntu 8.10. Before printing I checked the System Monitor application and I notice that I was only using 400MB out of 3GB. This is my first issue that I'm having with my printer and this is the only doc that I cannot print. The rest works fine ( with smaller docs)

The file that I'm trying to print is located here:
[http://www.firstnightraleigh.com/images/fnr09_event_map.pdf](http://www.firstnightraleigh.com/images/fnr09_event_map.pdf)

Thank you very much for your support!

AK

---

### Post by dcstar on 2008-12-31
> **arepaking said:**
> Hello Experts,
I've been trying to print a PDF (Doc size is 1.9MB) but I am not getting good results.

Every time I try to print, a sheet come out of the printer with the following message:

```
PCL5e ERROR - Insufficient Memory!!!!
 VERSION: PCL5e 1.35 10-20-2000
```

Now, I have a P4 with 3GB RAM running Ubuntu 8.10. Before printing I checked the System Monitor application and I notice that I was only using 400MB out of 3GB. This is my first issue that I'm having with my printer and this is the only doc that I cannot print. The rest works fine ( with smaller docs)

The file that I'm trying to print is located here:
[http://www.firstnightraleigh.com/images/fnr09_event_map.pdf](http://www.firstnightraleigh.com/images/fnr09_event_map.pdf)

Thank you very much for your support!

AK

Do you have sufficient disk space in /tmp ?

---

### Post by gsocker on 2008-12-31
That error message means the PCL interpreter in the printer does not have enough memory to print the document. It has nothing to do with the amount of memory in your computer.
1.9 MB is quite large for a single page of PDF. 

I'm guessing that you have a laser since most inkjets that use PCL(usually HP) don't go beyond PCL3 and usually don't print those kinds of messages. 

With a laser, the printer has to convert an entire page at a time into a giant bitmap. This implies that the printer needs to have enough memory built in to hold both 1 page of data sent from the computer AND the bitmap for the laser print engine. The file you are trying to print is apparently complex enough(or large enough) that the printer is running out of memory during the processing.

You might be able to print at "draft" resolution.

---

### Post by linux_tech on 2009-01-01
You could use the pdf2ps command to convert the pdf to ps
you can then use ghostcript to print the file
see here-
[http://tldp.org/HOWTO/Printing-Usage-HOWTO-3.html](http://tldp.org/HOWTO/Printing-Usage-HOWTO-3.html)

---

### Post by arepaking on 2009-01-01
> **gsocker said:**
> That error message means the PCL interpreter in the printer does not have enough memory to print the document. It has nothing to do with the amount of memory in your computer.
1.9 MB is quite large for a single page of PDF. 

I'm guessing that you have a laser since most inkjets that use PCL(usually HP) don't go beyond PCL3 and usually don't print those kinds of messages. 

With a laser, the printer has to convert an entire page at a time into a giant bitmap. This implies that the printer needs to have enough memory built in to hold both 1 page of data sent from the computer AND the bitmap for the laser print engine. The file you are trying to print is apparently complex enough(or large enough) that the printer is running out of memory during the processing.

You might be able to print at "draft" resolution.

Thanks gsocker, your explanation sounds very reasonable. And you were right, I have Laser printer (Samsung ML-6060).

---

