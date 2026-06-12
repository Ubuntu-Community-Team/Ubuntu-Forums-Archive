---
title: "[SOLVED] msn using pidgin"
date: 2009-01-12
forum: General Help
---

### Post by nzadLithium on 2009-01-12
Hey

Everytime before this pidgin has worked fine, but starting today it brings up the message "Unable to retrieve MSN Address Book", I have not downloaded any updates since last time I used it (to my knowledge).

In windows, via windows live messenger, I can connect fine. I tried amsn as well, but that tells me "Internal Error". 

Steps I've taken to attempt a fix:
rename .purple to .purple2 (so I can get it back if I need it :p)
remove pidgin and reinstall
sudo apt-get remove pidgin pidgin-data libpurple0
sudo apt-get install pidgin

upon doing this pidgin gave me some smiley lookup error and refused to start, its supposed to be a problem with libpurple and install order or something? But I can't remove libpurple without doing it exactly the same as I did before (dependencies), so I can't really do anything about that.

I then decided to compile the latest pidgin from source. I disabled network manager at configure time since I don't have network manager installed, and do not wish to install it. ./configure --disable-nm
then built it. All seems fine, I linked the pidgin binary to /usr/bin then started pidgin. It still tells me "Unable to retrieve MSN Address Book". Any ideas what I can do to fix it?

---

### Post by Ahadiel on 2009-01-12
Happening to me aswell (Archlinux Pidgin v2.5.3). Perhaps Microsoft modified the MSN Protocol?

---

### Post by gettinoriginal on 2009-01-12
I just tried mine, and MSN is disconnected for me too.  But aMsn is working fine for me.  I would almost bet it is microsoft doing another of their "windows live" things.  It messed up my hotmail account awhile ago, and had to make changes in Firefox configuration to correct that. ](*,)

---

### Post by Ahadiel on 2009-01-12
Related [bug report]("https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/316252").

---

### Post by gehzumteufel on 2009-01-12
I am also having a problem. Kubuntu 8.10 and Pidgin 2.5.3. It was working before I left for the weekend, and now it is failing.

As mentioned, I am sure it is an M$ change on their servers.

---

### Post by nzadLithium on 2009-01-12
Ah well nice to know its not just me :D Hope this is fixed fairly quickly :)

Thx peoples

Its possible that your amsn works coz you installed it from repos? I installed mine from the source developement version so I could get webcam plus voice chat :D

---

### Post by Ahadiel on 2009-01-12
If you urgently need MSN now, either install a different client or install 'msn-pecan'. Then change the account type in Pidgin to 'WLM' from 'MSN'.

---

### Post by hikaricore on 2009-01-12
I was connected until I disconnected to test this, same issue as all of you.  :p

@&%^ing Microsoft.

Bright side here.  I don't have to look at all that damn "message me on my other account cos I'm at work" spam we've all been getting for awhile.

---

### Post by Sunspore on 2009-01-12
just open terminal and type:

sudo apt-get install msn-pecan

Then change the account type in Pidgin to 'WLM' from 'MSN


I just tried, work for me.

---

### Post by Slate8 on 2009-01-12
Sunspore's workaround seems to have done the trick! Thanks :)

---

### Post by lunatico on 2009-01-12
Hi! Same issue here!!! Oh God do we hate M$ or what?! I do!
Anyway.... Ubuntu 8.10 and Pidgin 2.5.2... aMSN works fine...
I'll wait to see what happens during the day... maybe someone will come up with something...
Maybe we can all ditch MSN and switch to GTalk!!!
(sorry... I'm annoyed...)

---

### Post by lunatico on 2009-01-12
Yes Sunspore's workaround works. May I ask what is this doing? WLM? Safe to keep using this? Differences?
Cheers!

---

### Post by adamlau on 2009-01-12
Answer here: [http://ubuntuforums.org/showthread.php?t=1037515&page=3](http://ubuntuforums.org/showthread.php?t=1037515&page=3)

---

### Post by phorque on 2009-01-12
> **Ahadiel said:**
> If you urgently need MSN now, either install a different client or install 'msn-pecan'. Then change the account type in Pidgin to 'WLM' from 'MSN'.

result! worked straight away :) ty

---

### Post by hikaricore on 2009-01-12
It's just using a different protocol to sidestep the MSN server issue that the noobs at mickysoft caused. :p

---

### Post by nzadLithium on 2009-01-12
Pidgins msn is working now.

---

### Post by hikaricore on 2009-01-12
> **nzadLithium said:**
> Pidgins msn is working now.

Meaning microsock fixed their servers... good fun Sunday full of pissed off people.

---

### Post by Sunspore on 2009-01-12
your welcome Slate8, I just manage to find the solution slightly faster.

:-)
Cheerz

---

