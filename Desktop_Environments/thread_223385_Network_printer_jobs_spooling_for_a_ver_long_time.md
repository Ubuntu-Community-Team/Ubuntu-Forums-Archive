---
title: "Network printer: jobs spooling for a ver long time"
date: 2006-07-26
forum: Desktop Environments
---

### Post by kunal_nba on 2006-07-26
Hi, I work on a company and lately we are trying to migrate all our computers from Windows Xp to Ubuntu. We have 2 networks at our company, one for accounts and one for the internet.

I've got to solve almost everything, but I have a problem with the main printer. It's a HP ColorLaserjet 2500N printer, and has a HPJetDirect attached which we are using for the accounts network at our company.

Then there is a Longshine Print server attached to the printer also and we use it for our Internet Network. On this network at present we have a few windows machines and 4 machines which have been migrated to Ubuntu Dapper. So the problem is that when we send a job for printing from a Windows machine everything is ok but from the ubuntu machines.. when cups gets the job, it takes a very long time spooling, so it takes hours to print one of our 100+ pages PDF catalogs. The same thing occurs with OpenOffice documents or anything that has pictures.. just the text files print fast. When you send a job and go to printer properties you can see the message spooling xx% , and it's progress takes very long to finish. 

I would be very thankful if anyone could give me a solution. I configured the printer this way. Went to cups administration, and added a LPD printer.. typed the Ip adress of the print server, then selected the printer model.. HP2500N, and selected the driver.. hplip. I also installed the latest Hplip I downloaded from the official website and tried it, and also tried with the postscript driver, but all have the same problem.. we can print the jobs, but it takes just too long. So people over here are getting very frustrated, complaining and saying they want to return to windows. The problem is slowing down our job a lot. Personally I use Linux at home for years, and I want to apply this in the company, but have to get this issue solved.

Thanks in advance for your support.

---

### Post by shawnbishop on 2006-08-18
Good Day

I am having the same problem at an Architect firm, I installed a Ubunut Print Server to replace the Windows XP one as it could only take 10 connections at a time. Now to print a 532K Adobe Acrobat file takes almost 20 minutes!!

I have tried to update hplip from 0.9.5 to 1.6.7 useing apt-get but it wont upgrade form the backports archives.

I dont want to install it myself from source as when I try to remove theinstalled hplip it wants to remove the ubuntu-desktop files as well.

I tried to downgade the Acrobat reader from 7 to 5 but still the same problem, so it is an issue on the Print Server.

I have requested a baclport to update the hplip drivers

Cheers

---

