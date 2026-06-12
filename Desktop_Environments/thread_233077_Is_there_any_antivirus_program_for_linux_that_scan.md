---
title: "Is there any antivirus program for linux that scans files for windows viruses?"
date: 2006-08-09
forum: Desktop Environments
---

### Post by FreDeas on 2006-08-09
Hi, doesn't anybody has any idea?

---

### Post by bscbrit on 2006-08-09
Clamav is available in the repos as are several others.  It can be easily integrated into Evolution to check email traffic.

---

### Post by tzulberti on 2006-08-09
I think that there is also a version of AVG antivirus for linux. Search in the how-to section for more information about this.

---

### Post by FreDeas on 2006-08-09
I have clamav installed but does it scan for virus that afect winodws XP as well or not?

---

### Post by azmrb on 2006-08-09
Sophos has a version of their antivirus that scans both filesystem types.

---

### Post by bscbrit on 2006-08-10
> **FreDeas said:**
> I have clamav installed but does it scan for virus that afect winodws XP as well or not?

It scans for all viruses that are in its database.  That will include thousands of XP viruses.

---

### Post by computergroove on 2006-08-10
I tried to do what you are probably trying to do. I own a computer store and I am tired of having to pay license fees to Microsoft so I use Linux as much as I can. However I need a windows machine to scan for viruses on other peoples machines. I have not found an equal or better solution than to just have a windows machine running Norton to scan for viruses on these hard drives. DOnt flame me for using Norton I am well aware of the latest news regarding new spyware and viruses and the most popular virus software. Why do you want to check for viruses for windows machines on Linux?

---

### Post by bscbrit on 2006-08-10
> **computergroove said:**
> I tried to do what you are probably trying to do. I own a computer store and I am tired of having to pay license fees to Microsoft so I use Linux as much as I can. However I need a windows machine to scan for viruses on other peoples machines. I have not found an equal or better solution than to just have a windows machine running Norton to scan for viruses on these hard drives. DOnt flame me for using Norton I am well aware of the latest news regarding new spyware and viruses and the most popular virus software. Why do you want to check for viruses for windows machines on Linux?

The OP didn't mention this requirement.  _If_ (s)he is trying to scan disks formatted as NTFS then they will have limited success.  If it detects a virus there is not much that the software can do to remove it but, perhaps, knowing that there is a virus present is half the battle. (I would have assumed that 'yes' would be the normal state of affairs for most computers brought in for repair but perhaps that is my bias showing.)

I do precisely the same thing when I repair computers (not professionally!) but I have had more success with the free version of AVG - again that is just a personal preference.

However, if the OP simply wants to be a responsible citizen and simply take steps to ensure that they never send someone else a virus then the other suggestions in this thread should all help.

---

### Post by FreDeas on 2006-08-10
I'm not trying to scan ntfs. I just have an amd dual booted running both linux and XP. The problem is that I download lots of software and files from linux that I plan to install or run in windows. What I want is the possibility to scan everything when it's downloaded in linux so I no longer have to scan them under windows. 
Under windows I use a lot of cpu and memory consuming programs. Now I have avast installed and running continuasly and because it needs to update I have to connect to the internet and use firewalls and that stuff as well.
What I need is to scan everything on linux before I pass then on windows so I can get rid of all the antivirus spywares firewalls internet stuff etc that consume precious cpu.
Apart from that I do want to ensure that when I pass sth to a friends computer otr send an email I wan't pass him any dangerous virus as well..

So what I understanded is that with clamav I can do what I want, it just needs updating, right?

---

### Post by maniacmusician on 2006-08-10
Right. you should be all set with ClamAV

---

