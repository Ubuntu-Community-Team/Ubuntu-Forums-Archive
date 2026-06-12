---
title: "Looking for anti-virus for Ubuntu 6.06"
date: 2006-09-27
forum: Desktop Environments
---

### Post by tigerdivision on 2006-09-27
Hi all!

I am currently using Ubuntu 6.06 and I am looking for an anti-virus freeware product that runs under Ubuntu. Can someone please recommend such a product? I tried installing Panda Anti-Virus for Linux but couldn't find out how to install it under Ubuntu. 
Your help would be much appreciated.

Thanks

---

### Post by wieman01 on 2006-09-27
AVG. Great stuff. Good howto:

[http://www.ubuntuforums.org/showthread.php?t=136064&highlight=howto+avg]("http://www.ubuntuforums.org/showthread.php?t=136064&highlight=howto+avg")

---

### Post by sabitha on 2006-09-27
another post to install antivirus search with google :)

[http://allyourtech.com/content/articles/15_01_2006_installing_antivir_with_on_access_scanning_in_ubuntu_linux.php]("http://allyourtech.com/content/articles/15_01_2006_installing_antivir_with_on_access_scanning_in_ubuntu_linux.php")

---

### Post by Predius on 2006-09-27
You don't need to! There are virtually no viruses under Ubuntu. 

If you want to scan your Windows partition, you can always use ClamAV.

---

### Post by wieman01 on 2006-09-27
> **Predius said:**
> You don't need to! There are virtually no viruses under Ubuntu. 

If you want to scan your Windows partition, you can always use ClamAV.
That's a dangerous statement... The main reason why virus scanners for Linux ARE important is that unprotected Linux machines act as distributors of viruses and spread them when other Windows machines connect to them. So you DO need a virus scanner.

---

### Post by pseudonym on 2006-09-27
I use f-prot. There's a nice howto for installing the GUI version [here]("http://www.ubuntuforums.org/showthread.php?t=88357&highlight=f-prot").

You've just had four recommendations for great anti-virus software, none of which will cost you a penny. Dontcha love linux!

---

### Post by CaveRat on 2006-09-27
Make that five:

[http://www.avast.com/eng/download-avast-for-linux-edition.html](http://www.avast.com/eng/download-avast-for-linux-edition.html)

Been using Avast for a few years now. They have a deb package. You will need to register which is nothing new, but it is also free for home use.

---

### Post by az on 2006-09-27
> **wieman01 said:**
> That's a dangerous statement... .

No it's not. 

> **wieman01 said:**
> The main reason why virus scanners for Linux ARE important is that unprotected Linux machines act as distributors of viruses and spread them when other Windows machines connect to them..

By default, Ubuntu does not listen to the network - to upload a malware file to a windows machine, you would have to do it by hand. 

There is no need to run any antivirus or other anti-malware software on an Ubuntu desktop.

Just keep up to date with security updates.


> **wieman01 said:**
> 

 So you DO need a virus scanner.

Perhaps on a mail server, but not in general.  

As far as I am concerned, I have better things to do with my CPU cycles that to waste them looking for windows malware.

---

### Post by DougieFresh4U on 2006-09-27
Ok, for kicks I downloaded avast4 and now its with archive manager. What exactly do I need to do to open and install. thanks

---

### Post by wieman01 on 2006-09-28
> **azz said:**
> As far as I am concerned, I have better things to do with my CPU cycles that to waste them looking for windows malware.
That's a question of attitude. Plus there are Linux viruses around. You may decide to enable a virus scanner on demand, I have to agree here, but you do need one because there are viruses targeted at Linux systems. It's as easy as that. Why run the risk?

---

### Post by orb9220 on 2006-09-28
Well I see your point if you want to like wear a raincoat in the desert for that day when it will rain.

1) Linux viri are RARE and FEW (for now anyway that could change)

2) Even if a windows virus somehow got admin privileges to install on a  linux machine it could NOT pass itself on or propagate because it is windows code which cannot execute on linux machine. It would just sit  there.

3) The very nature of Linux machines makes it extremely difficult to  infect a machine. Most of the time it is a user that does not know what they are doing and allows one to be installed and agian I shall mention this is extremelly rare.

4) Most long-term user's that have posted have said time and time again. You do not need antivirus unless You are running a mail,file,web server where you are dealing with email or possible infected files. This is for the benifit of window user's not linux user's.

Please give any feedback on any inaccuracies,half-truth's,or plain wrong statements in this post. And in no way consider myself an expert just want to share accurate knowledge so the individual can make an informed choice.

---

### Post by wieman01 on 2006-09-28
> **orb9220 said:**
> Well I see your point if you want to like wear a raincoat in the desert for that day when it will rain.

1) Linux viri are RARE and FEW (for now anyway that could change)

2) Even if a windows virus somehow got admin privileges to install on a  linux machine it could NOT pass itself on or propagate because it is windows code which cannot execute on linux machine. It would just sit  there.

3) The very nature of Linux machines makes it extremely difficult to  infect a machine. Most of the time it is a user that does not know what they are doing and allows one to be installed and agian I shall mention this is extremelly rare.

4) Most long-term user's that have posted have said time and time again. You do not need antivirus unless You are running a mail,file,web server where you are dealing with email or possible infected files. This is for the benifit of window user's not linux user's.

Please give any feedback on any inaccuracies,half-truth's,or plain wrong statements in this post. And in no way consider myself an expert just want to share accurate knowledge so the individual can make an informed choice.
You're statements are all correct as far as I can tell. And I agree, viruses are rare and it's extremely unlikely that any of them will ever do harm to your system, however, I am equally concerned about my personal files in the home folder (open office documents, etc.) that may get lost in the process. I am not an expert but does that make sense?

Good discussion by the way.

---

### Post by asplode on 2006-09-28
From [wikipedia]("http://en.wikipedia.org/wiki/Plural_of_virus"):

> In the English language, the standard plural of virus is viruses. This is the most frequently occurring form of the plural, and refers to both a biological virus and a computer virus.

The less frequent variations viri and virii are virtually unknown in edited prose, and no major dictionary recognizes them as alternative forms. Their occurrence can be variously attributed to hypercorrection formed by analogy to Latin plurals such as radii; idiosyncratic use as jargon among a group, such as computer hackers; and deliberate word play, such as on BBSs (see, e.g.: leet).

To complicate matters further, viri is already used in Latin as the plural of vir, meaning "man" (thus making viri mean "men").

Not to be a grammar nazi.

Also, there are what?  6-7 linux viruses, and 4 of them were made in a lab/clean room environment?  Versus how many windows viruses?

---

### Post by wieman01 on 2006-09-28
Ok, I did a bit more reading and most of the sources confirm that it is not necessary to install a antivirus software on a PC that does not serve as a file or email server.

There is an interesting article here: [http://www.securityfocus.com/columnists/188]("http://www.securityfocus.com/columnists/188")

And the number of Linux viruses is roughly 40. Just to sum this up.

---

