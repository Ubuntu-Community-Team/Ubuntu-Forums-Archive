---
title: "Remote Access Help"
date: 2005-09-23
forum: Desktop Environments
---

### Post by Cl1maX on 2005-09-23
Hi All,

Ive bene using Hoary for the last 6 months and have loved it.  Recently however i deceide to try and use the remote access (VNC) frmo my ubuntu box at work to view and control my ubuntu box at home.

I installed ssh on my home machine and work machine and forwarded the port 22 on my router to my 192.168.2.5 linux box on the home network.  I then at work pinged my router.  Success!  and tryed to ssh on port 22.  Failure :< Connection refused.  I tried a few more times and ran nmap on my router to make sure the port was open.  After running nmap and trying to ssh a few more times I could no longer ssh and get conneciton refused nor when i tried could i ping my router.  My freinds could however stil ping the box and i could see myself on quakenet irc so the machine was still active.  
When i got home I realised on the work Pc i grabbed ssh and sshd and forgot to get sshd on the home box.  No wonder I was getting connection refused the ssh server wasnt active :)  I went into synaptic installed sshd and made sure It was wortking by using a local 192.168. machine to ssh into  it. 

Excellent ....

however I still cannont ping my machine remotely from my work ip.  I presume the box presumed it was being attacked because of my multiple differnet argumented ssh attempts and banned my ip...  

Have you got any idea how fix this ? 

Im going insane....  I think its more likely the router howevr looking through the routers web pages i couldnt see anything like a ban list or anything with my work pcs ip on it.  IM hoping its ubuntu being clever rarther than my router being insane esp as i cant seem to find the ban list on the router pages.

Any help is appreciated :)

My router is a belkin  :? ADSL modem with wireless g router.  IM not using wireless.

Many thanks in advance for helping :)

Cl1maX

---

### Post by Cl1maX on 2005-12-21
*** Bump ***

i coudl really do with this working please :s

cheers

---

