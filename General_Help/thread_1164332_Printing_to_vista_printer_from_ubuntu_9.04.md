---
title: "Printing to vista printer from ubuntu 9.04"
date: 2009-05-19
forum: General Help
---

### Post by eschulz on 2009-05-19
I need help with this. I have tried everything that I can find on the net about this problem and nothing seems to work. I have ubuntu 9.04 on my Dell D610 laptop and I have installed through SMB my HP D1320 printer that is being shared on my Vista box. Ubuntu sees the printer just fine and when I try to do a test print, ubuntu says that it printed, but when I look at the printer on my vista system it says that there is still a job in the print queue, and nothing will print. The printer seems like it will print (head moves back an forth and then the printer light will start blinking like it is reciving data, but then nothing happens, and for me to get it out of the print queue on the vista system I have to remove the printer from the system and reinstall it. Any ideas.

Thanks

---

### Post by cariboo on 2009-05-19
Do you have the correct driver installed on Ubuntu for your printer? Because I don't see a driver listed for your printer under Dell in the Printing wizard.

---

### Post by Concrete on 2009-05-19
> **eschulz said:**
> Ubuntu sees the printer just fine and when I try to do a test print, ubuntu says that it printed, but when I look at the printer on my vista system it says that there is still a job in the print queue, and nothing will print. The printer seems like it will print (head moves back an forth and then the printer light will start blinking like it is reciving data, but then nothing happens, and for me to get it out of the print queue on the vista system I have to remove the printer from the system and reinstall it.

This is simptom's whe u using unmatched driver for ur printer. If u wont to get all printers work 1/1 u must select and install working driver  just for your version and model of printer...

---

### Post by eschulz on 2009-05-20
I am using the d1300 series printer driver. I have my vista computer dual booted with ubuntu, and when I am in ubuntu with the same printer driver it work just fine and the laptop will print as well. I know that I could just stay in ubuntu and be done with it, but there has to be a way to get this to work, also I have not converted the wife over to ubuntu yet so I have to keep the vista running.

---

### Post by PerfectReign on 2009-06-01
Not sure how to help you here. 

I have had the same issue. I posted my question over on Linuxquestions.org - [http://www.linuxquestions.org/questions/linux-general-1/problem-printing-to-vista-shared-printer-725594/?posted=1](http://www.linuxquestions.org/questions/linux-general-1/problem-printing-to-vista-shared-printer-725594/?posted=1) - and have not been able to solve.

Oddly enough, printing from my laptop to my work Vista computer (sharing an HP LaserJet 1320) works fine, but printing to my wife's Vista computer (sharing an HP OfficeJet 5600 all-in-one) fails.

Based on a response from LinuxQuestions, I hooked up my laptop directly to my wife's printer and successfully printed.  I expected it might have been a driver problem, but since it prints fine directly, that can't be it.

---

### Post by rcayea on 2009-06-01
I have the same issue with printing from my ubuntu box to my wife's printer which runs Vista. 

I set up via simba and I go through the whole process and I still can't print, just as you described above.

---

### Post by PerfectReign on 2009-06-01
Hmm. 

I wonder if there's something in the non domain or active directory networking prohibiting a print job.

Oh, I can print from this laptop no problem also to any of several HP network printers - LaserJet 5500, LaserJet 9000...

---

### Post by smapdi636 on 2009-07-25
I'm having the same problem.  9.04 to a HP d1320 shared on XP.

---

