---
title: "i might get laughed at for asking, but..."
date: 2005-04-17
forum: Desktop Environments
---

### Post by graigsmith on 2005-04-17
So i recently ditched windows.  do i need a virus scanner?   :razz:

---

### Post by carlc on 2005-04-17
This would depend entirely on who you ask. I have never used one in windows or Linux.   
I would think most people who use Linux do not use virus scanners, but I guess it would not hurt.

---

### Post by GOwin on 2005-04-17
I think a firewall in Linux should be the first thing to consider rather than an anti-virus.

---

### Post by bored2k on 2005-04-17
I think 95% of Linux users don't need any type of antivirus. I have never seen any destructive software doing damage to the masses like worm.melissa or pe.funlove or bill.gates :roll:. I'm a user who likes to test things a lot, and the most damage my computer has received have been consequences of my own actions (like typing by mistake "rm -rf * .transgaming*" <-- don't do it by the way). Most of the users would agree I think, but, if you're running a corporate server, a little extra security won't do you any harm ;).


And by the way, making fun of fellow members is not something we encourage.

[http://www.ubuntuforums.org/faq.php?](http://www.ubuntuforums.org/faq.php?)
>  1. Be polite. This is a end user forum community, moderated by ubuntu users.

---

### Post by graigsmith on 2005-04-17
well, this is just my home desktop computer.  And my router is already filtering nearly every port except for things i use.

i have a personal ftp server running, and the ports are open.  is there a logfile i can check to see if i am getting hundreds of failed login attempts?

---

### Post by bored2k on 2005-04-17
[QUOTE=graigsmith]well, this is just my home desktop computer.  And my router is already filtering nearly every port except for things i use.

i have a personal ftp server running, and the ports are open.  is there a logfile i can check to see if i am getting hundreds of failed login attempts?[/QUOTE]
 I suggest you install firestarter. It's easy to use, keeps a log file and it's always on by default [even If you don't see a running GUI].

[http://ubuntuguide.org/#firestarter](http://ubuntuguide.org/#firestarter)
[http://ubuntuforums.org/showthread.php?t=26483&highlight=firestarter+adm](http://ubuntuforums.org/showthread.php?t=26483&highlight=firestarter+adm)

---

### Post by graigsmith on 2005-04-17
is fire starter the kind of firewall that will block someone after so many attempts?

---

### Post by Bob D. on 2005-04-17
[QUOTE=graigsmith]So i recently ditched windows.  do i need a virus scanner?   :razz:[/QUOTE]
I believe some folks install virus scanners on Linux, not so much to protect themselves, but to keep from passing viruses on to Windows-using friends via email.

Bob

---

### Post by denzilla on 2005-04-17
[QUOTE=Bob D.]I believe some folks install virus scanners on Linux, not so much to protect themselves, but to keep from passing viruses on to Windows-using friends via email.

Bob[/QUOTE]

I was about to bring that up. Linux users don't fear viruses, but isn't it somewhat irresponsible for us to pass potentially infected files to a windows user?

---

### Post by az on 2005-04-17
[QUOTE=denzilla]I was about to bring that up. Linux users don't fear viruses, but isn't it somewhat irresponsible for us to pass potentially infected files to a windows user?[/QUOTE]

Actively?  Yes.  If you know that a file is a virus, you should delete it.

Passively?  No.  Am I going to scan my entire hard disk to look for these?  Given the fact that there is much less of a chance that someone can access my Ubuntu machine since it is not listening, it would not make much sense.  Other OS's shortcomings do not keep me awake at night.
Now, if I were running a mailserver, it would probably be good business sense since I would want to keep my customers...
It depends on what you do with your ftp server.

---

### Post by jordanau on 2005-04-17
I have always wondered, are there any linux viruses in existence? If so, do fixes get made quicly enough to stop them? Why is nobody writing linux viruses?

---

### Post by tread on 2005-04-18
Here's a partial answer (it's all I can remember anyway :))

A user cannot spread a virus within his own system, since it would run with his privileges which means that it cannot affect any of the binaries owned by root. The virus could affect the binaries owned by the user, but typically, these would be very few.

Despite this, of course, it would be possible to write a virus anyway .. say by a buffer exploit. But since security patches are so common due to open source, these would get fixed quickly (hence, we need to apply patches regularly :) .. and the really paranoid should stick to debian stable!) 

Hmm .. that makes sense. There you go :)

---

### Post by az on 2005-04-18
There are linux viruses.  But people say virus when they probably mean a whole variety of security exploits....

---

### Post by Stormy Eyes on 2005-04-18
[QUOTE=jordanau]I have always wondered, are there any linux viruses in existence? If so, do fixes get made quicly enough to stop them? Why is nobody writing linux viruses?[/QUOTE]

There are, but they usually require root privileges in order to do their dirty work. You're more likely to see rootkits and buffer overflow exploits.

---

### Post by ubuntu27 on 2005-04-26
Well, Yeah. Like our brother and sis said (We all are Ubuntu users!!) said, Linux is far more secure than William Henry Gates III 's Windows..

But, I was surprised to see that there was endeed Antivirus for Linux. see the folowing:

Antivirus Server in Unofficial Ubuntu Guide:

[http://ubuntuguide.org/#antivirusserver](http://ubuntuguide.org/#antivirusserver)

So, there is an antivirus called "ClamAV AntiVirus"

Then, look! Here goes Panda!! Panda Antivirus for Linux!! 
[http://www.pandasoftware.com/download/linux/linux.asp](http://www.pandasoftware.com/download/linux/linux.asp)

BitDefender for Linux:

[http://www.bitdefender.com/index.php?tab=2](http://www.bitdefender.com/index.php?tab=2)

F-Prot Antivirus for Linux (for home users):
[http://www.f-prot.com/products/home_use/linux/](http://www.f-prot.com/products/home_use/linux/)


McAfee Linux Shield:
[http://www.networkassociates.com/us/products/mcafee/antivirus/fileserver/linuxshield.htm](http://www.networkassociates.com/us/products/mcafee/antivirus/fileserver/linuxshield.htm)

Kaspersky Antivirus:
[http://www.kaspersky.com/businessoptimal?chapter=4158433](http://www.kaspersky.com/businessoptimal?chapter=4158433)

List of Antivirus service for Linux: [http://www.linux.org/apps/all/System/Anti-Virus.html](http://www.linux.org/apps/all/System/Anti-Virus.html)

Linux Antivirus Services:
[http://www.e-zest.net/linux-server-antivirus.htm](http://www.e-zest.net/linux-server-antivirus.htm)
********

Well, I've never tried Antivirus for Linux... I am jsut giving the links, so you may explore, and try it, if you want.

---

### Post by thecrimsonking on 2005-04-26
I have run linux without a firewall and without antivirus for years and have never had a single problem.  Nor do I spent a second worrying about any of my linux pc's security.
Of course, I am behind a router and use NAT though.

[QUOTE=azz]Other OS's shortcomings do not keep me awake at night.[/QUOTE]

Couldn't agree more.  If you choose to run Windows, it's YOUR responsibility to safeguard your system.   Quit whining about all of Windows vulnerabilities and security flaws and switch to a REAL OS.

Linux:  because a pc is a terrible thing to waste.

---

### Post by LongTooth on 2005-04-27
I've been a Linux user since 1999 and have had no use for virus software. But like others have stated, you just might recieve some crap you pass on to a friend. Like everyone on the net, I'm sure that you have a buddy that passes on every email joke or what ever he get from god knows who. In a case like this it will not infect your machine but if it does have a virus and you do pass it on...well, what can you say? For this reason I pratice save internet. I don't, and I mean don't, pass this well meaning but unsafe junk to friends. I especially don't do this on my family's Win machine. But to get back to Linux and virii, I don't think you have anything to worry about...yet!

If it was up to me, I'd horse whip every script kiddy out there. Then maybe this nonsense will stop. But that just my point of view.

---

### Post by graigsmith on 2005-04-27
thanks for the replies everyone ;)

---

### Post by crazybill on 2005-04-27
Yes, you should install an antivirus.

Check out the CLAM ANTIVIRUS SECTION of [http://home.cvc.org/ac/learningUNIX.htm](http://home.cvc.org/ac/learningUNIX.htm)

---

### Post by matchstich on 2006-12-11
i have firestater and avast

---

### Post by az on 2006-12-11
> **crazybill said:**
> Yes, you should install an antivirus.

Check out the CLAM ANTIVIRUS SECTION of [http://home.cvc.org/ac/learningUNIX.htm](http://home.cvc.org/ac/learningUNIX.htm)

No!  Just keep up-to-date with security updates.

---

