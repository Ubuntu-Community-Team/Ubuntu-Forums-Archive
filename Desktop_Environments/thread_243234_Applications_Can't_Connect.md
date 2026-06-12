---
title: "Applications Can't Connect"
date: 2006-08-24
forum: Desktop Environments
---

### Post by RurouniKenshinX on 2006-08-24
I have searched everywhere and can not find a solution.  I was hoping someone here might be able to answer it for me.

First off before anyone jumps to conclusions, I do have a connection to the internet, and have downloaded updates.

Now, here's my problem.  All of my programs can NOT connect to the internet.  After I installed all the updates firefox loaded Google ONCE, and that's been all i can get out of applications.  If anyone can help, it'd be greatly appreciated!

Also, i can't mount my harddrives other than the linux ones, it gives me a permissions error of some sort.  Any help on that one too I'd greatly appreciate.

---

### Post by skcoyote on 2006-08-24
Unfortunately, you really haven't given us much to go on. If I read your post accurately, you're saying some of your programs can't communicate successfully with remote hosts--sometimes. You'll get more useful replies if you include some specific examples of what you've tried, what specific symptoms lead you to believe it doesn't work, and what your network configuration looks like.

Can you access hosts by IP address, but not by name (in which case you'd have a DNS issue)? Can you ping the IP of your immediate uplink? What about the hop after that? Are you on dialup, cable, DSL, some kind of LAN (including shared DSL or cable), or are you using homing pigeons carrying high density optical media for your last mile technology?

If it's the latter, it's possible that your packet loss is being caused by a neighbour with a shotgun.

You also asked a completely unrelated question about hard disk drives. I'd recommend posting that in a separate thread.

---

### Post by RurouniKenshinX on 2006-08-25
I have found that disabling IPV6 within firefox allows me to connect to websites, and I also discovered that IPV6 has been set as the localhost on my computer.  I am very confident that changing this all to be IPV4 would fix this, however, I am not sure how to do this as it does not let me.  Furthermore, I have always been a windows user and programmer, so adapting to a new operating system isn't very easy.  If you would please provide instructions and details as to what i can provide you with, it would help me

---

### Post by Monster Boxx on 2006-08-25
I am having similar problems. I however do not have connection to the internet at all. I can ping the router and other PCs. I have the DNS configured correctly. I have one NIC (Eth0) this is all setup, it is also my "gateway device". So in turn I am not able to install openssh-server so I can configure from my comfy chair. Ubuntu is running on a big loud fileserver, in addidition to me having to stand...

Enough of my sob stories, I just need to be able to connect to the internet. Is there something i am missing?

and yes I am sure the DNS is setup properly, this is the same way I  have configured all the computers on my network, including the one I am posting on

DNS was indeed setup properly...though working on windows for a good chunk of my life I confused myself by setting the gateway address with a DNS address(not reading just typing away) problem solved and no issues...

---

### Post by RurouniKenshinX on 2006-08-25
> **Monster Boxx said:**
> I am having similar problems. I however do not have connection to the internet at all. I can ping the router and other PCs. I have the DNS configured correctly. I have one NIC (Eth0) this is all setup, it is also my "gateway device". So in turn I am not able to install openssh-server so I can configure from my comfy chair. Ubuntu is running on a big loud fileserver, in addidition to me having to stand...

Enough of my sob stories, I just need to be able to connect to the internet. Is there something i am missing?

and yes I am sure the DNS is setup properly, this is the same way I  have configured all the computers on my network, including the one I am posting on

DNS was indeed setup properly...though working on windows for a good chunk of my life I confused myself by setting the gateway address with a DNS address(not reading just typing away) problem solved and no issues...

set your internet connect to DHCP and see if you can atleast get updates, that's what i did

---

### Post by RurouniKenshinX on 2006-08-25
*BUMP* it's been 12 hours and at this point i am willing to leave someone a small tip if they can solve my problem.

---

### Post by RurouniKenshinX on 2006-08-26
*BUMP* I can really use some help guys, if anyone can solve this i'd be eternally greatful!

---

