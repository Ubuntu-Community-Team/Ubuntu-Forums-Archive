---
title: "Secondary School network issues for extra-curricular Ubuntu"
date: 2007-10-15
forum: Education &amp; Science
---

### Post by falkorech on 2007-10-15
I am a teacher in one of the largest comprehensive schools in England.  We have an ‘Activities Week’ every July, when the normal school timetable is suspended and students can opt for an extra-curricular course.  I want to run an Ubuntu familiarisation course for students aged 14 and 15.  The school has a number of unused Intel Pentium III machines which run Windows XP Professional.  They are old but operational.  I would like to give students the opportunity to download and install Ubuntu as a replacement operating system in those machines and then go on to investigate some of the resources available through the Ubuntu repositories.  The School’s Sytems Manager is in favour but his senior technician is only prepared to support the idea under the proviso that none of the machines are connected to the school network.  Her view is that “he can install Ubuntu on any machines we have available, but on no account can he put a network cable into them and connect them to our network, for Internet access or anything else. Ubuntu ignores Windows permissions, and the students would have free rein over all the network.”
I have installed Ubuntu (Dapper Drake 6.06 LTS) onto two of my own home systems and have been amazed with, and greatly impressed by Ubuntu.  I want to share my enthusiasm with students but I do not have the network expertise to counter the arguments of the School’s Senior Technician.  Can anyone help.  It would be such a pity if our school closed this potentially open door on Ubuntu.

---

### Post by macgar32 on 2007-10-16
Ubuntu does not ignore windows permissions on the network.  Only on the local hard drive.

Any shares that are protected by windows persmissions on the network will still be protected.

---

### Post by jonathonblake on 2007-10-17
>   Her view is that “he can install Ubuntu on any machines we have available, but on no account can he put a network cable into them and connect them to our network, for Internet access or anything else. Ubuntu ignores Windows permissions, and the students would have free rein over all the network.”

I realize that Windows and security are mutually exclusive terms.

But if an Ubuntu installation is going to run rampant over their network, exposing everything, then the issue is the incompetence of the Windows Network Security Administrator, not Ubuntu ignoring permissions.  

Ubuntu does honour Windows permissions. 

> not have the network expertise to counter the arguments of the School’s Senior Technician.  Can anyone help. 

Get the senior Technician with you, and use a Live CD on one of those Pentiums, to show how exploitable the system is. (You might want to consider using Live CDs for the training session.)

xan

jonathon

---

