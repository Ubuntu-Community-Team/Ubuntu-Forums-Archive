---
title: "I need an Antivirus"
date: 2006-01-16
forum: Desktop Environments
---

### Post by shade11 on 2006-01-16
I need an antivirus for Ubuntu and I don't know what to get.

-I downloaded Panda Antivirus and I don't know how to update it.
-I downloaded BitDefender and It doesnt work.
-I downloaded Avast and I didnt know how to use it at all and it looked like it wasn't installed at all.

Can someone please tell me how to fix these problems or tell me of another Antivirus. I still need an antivirus. Even if I am running Linux

---

### Post by dcstar on 2006-01-16
[QUOTE=shade11]I need an antivirus for Ubuntu and I don't know what to get.

-I downloaded Panda Antivirus and I don't know how to update it.
-I downloaded BitDefender and It doesnt work.
-I downloaded Avast and I didnt know how to use it at all and it looked like it wasn't installed at all.

Can someone please tell me how to fix these problems or tell me of another Antivirus. I still need an antivirus. Even if I am running Linux[/QUOTE]
clamav

---

### Post by rfruth on 2006-01-16
I like clamAV, it seems to work well ! [https://wiki.ubuntu.com/ClamAV?highlight=%28clamav%29]("https://wiki.ubuntu.com/ClamAV?highlight=%28clamav%29")

---

### Post by lyly on 2006-01-16
Have clamav a permanent shield? or it can be used only to scan disks?

---

### Post by shade11 on 2006-01-16
I have tried ClamAV but I dont know how to use it. Can someone please tell me how to use it?

---

### Post by shade11 on 2006-01-16
Ok so I installed ClamAV and when I tried to run freshclam it gives me this message:

```
ian@Jevelxelwen:~$ freshclam
ERROR: Can't open /var/log/clamav/freshclam.log in append mode (check permissions!).
ERROR: Problem with internal logger.

```

Then I geve myself Root permissions:
```
root@Jevelxelwen:~# freshclam
ClamAV update process started at Mon Jan 16 15:51:55 2006
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.87.1 Recommended version: 0.88
DON'T PANIC! Read http://www.clamav.net/faq.html
main.cvd is up to date (version: 35, sigs: 41649, f-level: 6, builder: tkojm)
daily.cvd is up to date (version: 1243, sigs: 838, f-level: 6, builder: sven)
```

Is there someway to update it properly? Without downloading the new version without going to the website.

---

### Post by dcstar on 2006-01-16
[QUOTE=shade11]
......
Is there someway to update it properly? Without downloading the new version without going to the website.[/QUOTE]
Wait until the Ubuntu developers update it (which is usually in a few weeks).

---

### Post by qferret on 2006-01-16
I've been using Aegis as of late. I used to use F-Prot. How does clamav stack up?
Anyone out there that's tried both?

---

### Post by dcstar on 2006-01-16
[QUOTE=qferret]I've been using Aegis as of late. I used to use F-Prot. How does clamav stack up?
Anyone out there that's tried both?[/QUOTE]
I can't give much of a comparison, I just use clamav to scan all of my incoming Evolution e-mails, and then inform me of any of the various Windows Viri regularly detected in them.

It's really only for informational purposes, but it is handy to see what crap is out there (that doesn't affect Linux.........)            ;)

---

### Post by shade11 on 2006-01-16
I got clamav running for now. So I am happy. Thanks guys.

---

### Post by Almighty on 2006-01-17
[QUOTE=shade11]I got clamav running for now. So I am happy. Thanks guys.[/QUOTE]

So how did you fix it? I can up with the same error you did.

---

### Post by shade11 on 2006-01-22
the easiest fix ever. Get rid of it. You don't need an antivirus for Linux.

---

### Post by mchatel on 2006-01-23
It really bugs me when someone says "you don't need an antivirus program for Linux".  That's not a valid, or useful answer at all.  Some people may choose not to run an anti-virus program on a Linux system, but there is still need for them.  This user obviously has a need for one.

I realize there is less potential for a virus to strike a Linux machine, and to do any damage, but I don't think it's a good idea to just assume "I'm safe", just because virus writers haven't targetted you're OS.  No OS is safe.  Some OS's are just a lot more vulnerable than others.

Besides...  there are other systems to worry about.  I think *everyone* in this forum must e-mail Windows users...  and it would be proper computing practice not to pass on all your Windows-specific viruses to them.

I myself use ClamAV, for now.

---

### Post by slux on 2006-01-23
[QUOTE=mchatel]It really bugs me when someone says "you don't need an antivirus program for Linux".  That's not a valid, or useful answer at all.  Some people may choose not to run an anti-virus program on a Linux system, but there is still need for them.  This user obviously has a need for one.

I realize there is less potential for a virus to strike a Linux machine, and to do any damage, but I don't think it's a good idea to just assume "I'm safe", just because virus writers haven't targetted you're OS.  No OS is safe.  Some OS's are just a lot more vulnerable than others.
[/QUOTE]

When there's exactly zero viruses that have been ever reported in the wild the threat of catching a virus is pretty much zero. If some day the situation changes I'll be happy to start running some sort of virus scanner but for now it simply isn't worth the trouble and wasted system resources when it would just be scanning for viruses that don't affect Linux. I don't think Linux is as vulnerable to widespread epidemics as Windows either. The systems out there vary greatly. 

I don't walk around wearing a tinfoil hat either.

---

### Post by shade11 on 2006-01-23
The antivirus software ClamAV only scans for viruses that are Windows viruses. Antivirus software for Linux is for Linux PC's that are connected to networks. That way the network doesnt get infected. But usually the network has an antivirus of it's own. Even if, a virus can't usually go anywhere if it is on Linux.

Linux is practically impenitrable to viruses. Don't you think that the few viruses that were created to infect Linux weren't already patched yet?

---

### Post by redmansk8 on 2006-01-23
another antivirus software that works with linux is Anti Vir if you feel you need antivirus software. I installed it on Ubuntu and Mandrake 10.

---

### Post by mchatel on 2006-01-23
[QUOTE=slux]When there's exactly zero viruses that have been ever reported in the wild the threat of catching a virus is pretty much zero. If some day the situation changes I'll be happy to start running some sort of virus scanner but for now it simply isn't worth the trouble and wasted system resources when it would just be scanning for viruses that don't affect Linux. I don't think Linux is as vulnerable to widespread epidemics as Windows either. The systems out there vary greatly. 

I don't walk around wearing a tinfoil hat either.[/QUOTE]

No, there are more than zero viruses for Linux, that made it outside of an experiment.  Linux.RST.b is one that I can think of off-hand.  It was found in Korean contributed versions of Mozilla Suite 1.7.6 and also in Thunderbird 1.0.2, right off the Mozilla FTP sites.  They even posted a security notice about it, at the time.

Agreed, Windows and Linux systems vary greatly.  But I don't think that makes Linux impenetrable to virus threats.  Yes, it's a more secure OS, but then again, it's one that isn't as used widely as Windows.  The more Linux builds up a user-base, the more it will attract the attention of virus writers.  And the more attention they pay to it, the more they will find ways around Linux's security.

And like I said...  if people are e-mailing Windows users, they should do their best not to pass on infections to their Windows counterparts.

---

### Post by slux on 2006-01-23
[QUOTE=mchatel]No, there are more than zero viruses for Linux, that made it outside of an experiment.  Linux.RST.b is one that I can think of off-hand.  It was found in Korean contributed versions of Mozilla Suite 1.7.6 and also in Thunderbird 1.0.2, right off the Mozilla FTP sites.  They even posted a security notice about it, at the time.
[/QUOTE]

Right, I heard about linux.rst.b but thought it was more of a trojan. Now that I look at the description I do see why it could be classified as a virus and it's even been in the wild (albeit very, very limitedly). 

However, reading about it I realized that there's almost nonexistant chance a virus that infects executable files would ever infect a significant number of Linux machines because of the way software is distributed on virtually all GNU/Linux distributions. People don't go to a random website and download a bunch of binaries. Instead, their distribution packages software that is compiled specifically for the platform from source. These packages are also signed in for example Ubuntu so you won't get infected by a shady mirror either. Another feather in package management's hat.

> 
Agreed, Windows and Linux systems vary greatly.  But I don't think that makes Linux impenetrable to virus threats.  Yes, it's a more secure OS, but then again, it's one that isn't as used widely as Windows.  The more Linux builds up a user-base, the more it will attract the attention of virus writers.  And the more attention they pay to it, the more they will find ways around Linux's security.


What I actually meant was that different Linux distributions vary greatly as well. A virus that depends on a certain version of a certain piece of software being present will not find it in all installs. Ubuntu may be one of the more popular distributions out there but not a single one really dominates. Many Windows security holes are caused by very old architectural decisions and infinite desire for backwards-compatibility though. I'd say Linux has better chance not being exploited although I agree that viruses are a definite possibility for it too. Just not a threat for the time being.

> And like I said...  if people are e-mailing Windows users, they should do their best not to pass on infections to their Windows counterparts.

I'll rather not forward suspect mails and attachments. Anyway, I feel keeping their box clean is the responsibility of the person who has chosen Windows and not mine.

---

### Post by shade11 on 2006-01-23
Wasny there only 11 viruses made for Linux.

---

### Post by Perfect Storm on 2006-01-23
Read somewhere it was 6 but I don't know if it's true. Most of them labo-tests.

---

### Post by shade11 on 2006-01-23
Oh, well I was told it was 11.

---

### Post by dreadnought on 2006-01-23
I have to agree with mchatel re passing on virus via email. We should all do our best to stamp out this menace. I find it hard to understand the complacent attitude shown by some. You can rest assured  linux will start to be attacked when the brainless morons start to get to grips with the OS. I also do not agree with the Ubuntu team idea of not having a firewall set up by default.

---

### Post by detyabozhye on 2006-01-23
Again? It's been explained dozens of times why there are so few Linux viruses and why they are virtually harmless. 
[http://www.viruslibrary.com/virusinfo/Linux.htm](http://www.viruslibrary.com/virusinfo/Linux.htm)
[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)
[http://librenix.com/?inode=21](http://librenix.com/?inode=21)

---

### Post by Sirin on 2006-01-23
You could also try Aegis. :)

---

### Post by detyabozhye on 2006-01-23
BTW, if anyone wants a good laugh, check this out:
[http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

---

### Post by dcstar on 2006-01-23
[QUOTE=mchatel]
.......
Besides...  there are other systems to worry about.  I think *everyone* in this forum must e-mail Windows users...  and it would be proper computing practice not to pass on all your Windows-specific viruses to them.

I myself use ClamAV, for now.[/QUOTE]
Just on this, I was receiving many (many) Windows Viri that were being picked up by my ClamAV/Evolution setup, but now that I have my [enhanced]("http://ubuntuforums.org/showthread.php?t=96428") Spamassassin filtering working, most of these don't even get into my system now!    :p

Just goes to show how multi-layered defences are more useful than just relying on one layer.

---

### Post by detyabozhye on 2006-01-23
The only reason you would need an Antivirus on Linux is to protect Windows PCs on your network (depending on your Windows network setup, of coarse). If you dual boot, well, come on, are you going to try to run everything you download to Linux on Windows? Well, if you are, maybe you'll need an antivirus in that case.

The point is, you don't really need an anti-virus to protect your Linux box at the moment (and possibly for years to come).

---

### Post by detyabozhye on 2006-01-23
BTW, anybody have a Windows virus handy? I wanna play around with it on WINE, see how much WINE has improved in their 0.9.x series.

EDIT: This isn't a real virus, but it ran under WINE: [http://www.eicar.org/anti_virus_test_file.htm](http://www.eicar.org/anti_virus_test_file.htm)

---

### Post by rfruth on 2006-01-23
There was (is ?) a benign virus on the grisoft web site for testing purposes
[http://free.grisoft.com/doc/20/lng/us/tpl/v5]("http://free.grisoft.com/doc/20/lng/us/tpl/v5")

---

### Post by shade11 on 2006-01-24
People who use linux are usually knolegeable on bad Windpws viruses. At least I am.

---

### Post by briancurtin on 2006-01-24
[QUOTE=shade11]People who use linux are usually knolegeable on bad Windpws viruses. At least I am.[/QUOTE]
huh?

i know people who use linux who know nothing about windows at all (they claim they do), let alone the viruses on it.

---

### Post by r4ik on 2006-01-24
Reading this post and several others on the topic i question myself howlong it will take before Linux/Ubuntu is going to be hit by a major virus attack.
There will always be "people' who like to screw up things.
I can even imagine "people" getting bored on windows only.
So lets go do Linux.
It has been stated over and over agian it cant be done.
I find that highly questionable.
Knowing many people do not agree with this, i dont want to be the "nice guy" on the topic, i just want the best for the community.
So yes imo we do need antivirus or at least have one stored away for the big day.

---

### Post by detyabozhye on 2006-01-24
Linux's architecture makes it a lot harder on viruses to harm a system. So even though Linux viruses are possible, and we may need an antivirus in the future, the magnitude of the attack on Linux will never reach the magnitude of Windows's unless you do what Linspire did. Linspire is all right for noobs, but they copied some bad "features" from M$, like having the first account have superuser privelages by default.

---

### Post by shade11 on 2006-01-25
Doesnt Linux antivirus software only detect Windows viruses?

---

### Post by Animortis on 2006-01-25
I was sure I'd read it got the two known linux viruses too.

---

### Post by shade11 on 2006-01-26
I am sure that if I was to create and maintain a Linux antivirus, that it would include detection of viruses that effect Linux.

---

### Post by dreadnought on 2006-01-26
We know windohs viri will not harm a Linux system but what happens if you forward a third party email that has a virus embedded onto a windohs user?
That is why I believe we should run virus software to help stop this menace in its tracks.

---

### Post by detyabozhye on 2006-01-26
I personely deal with those manually, and I usually don't get more than one virus infected attachment per year.

---

### Post by shade11 on 2006-01-26
Most email services today have an antivirus on them. Gmail has one. And personally, I dont even send/recive viruses at all.

---

### Post by Thulemanden on 2006-01-27
Isn't it more a question of prevention, a pre-emptive strike.

I mean, if the virus writers know that every linux system is packed down hard with  free anti-virus, then they aren't motivated to even attempt it. Well, a few will see it as a challenge.

I just can't see why any Linux should even hit the streets without an AV and firewall includede and automatically setup. It just doesn't make sense.

By the way, I had 2 virus mailed quaranteened in Linux the other day. Caught be Xandros AV. 

(I later deleted Xandros and replaced it with this Hoary to mirror my newbie brothers Ubuntu I installed for him. Can't wait for the new 5 cd's of Breezy :-))

---

### Post by shade11 on 2006-01-27
[QUOTE=Thulemanden]Isn't it more a question of prevention, a pre-emptive strike.

I mean, if the virus writers know that every linux system is packed down hard with  free anti-virus, then they aren't motivated to even attempt it. Well, a few will see it as a challenge.

I just can't see why any Linux should even hit the streets without an AV and firewall includede and automatically setup. It just doesn't make sense.

By the way, I had 2 virus mailed quaranteened in Linux the other day. Caught be Xandros AV. 

(I later deleted Xandros and replaced it with this Hoary to mirror my newbie brothers Ubuntu I installed for him. Can't wait for the new 5 cd's of Breezy :-))[/QUOTE]

Linux antiviruses are for servers and people who send alot of files. Linux could get a Windows virus but it wouldnt work on it. And also, there arent many Linux viruses out there. You are secure you are running linux do not worry. The ony security thing you may need is a firewall.

---

### Post by detyabozhye on 2006-01-27
[QUOTE=Thulemanden]By the way, I had 2 virus mailed quaranteened in Linux the other day. Caught be Xandros AV.[/QUOTE]
But the viruses were for Windows, weren't they?

Linux itself just doesn't need an antivirus at the moment because it's *almost* impossible to infect it. If you also run Windows, and if you want to download stuff to via Linux to run it on Windows, then an AV might come in handy. But just like that, it'll just be eating your resources for no good reason, IMO.

---

### Post by Thulemanden on 2006-01-27
I wonder if people saying virus won't bite on a linux have considered that some users may actually run their Linux as root all the time? (And I am not talking MS virus)

Wouldn't that make a difference?

---

### Post by detyabozhye on 2006-01-27
Yes, that would. In that case, you have a user who needs a little education. If you run Ubuntu with it's default config, you don't have that problem. But then again, there is a very smal number of Linux viruses, AFAIK, only one has been seen in the wild so far, so even then, it'll take a loooooooooooooooooooooooooooong time before he gets one (unless he searchesfor one himself).

---

### Post by veritas366 on 2006-01-28
I just ran a clamscan.  It says I have 5 viruses.  Unexpectedly, they aren't even in my home folder as I scanned that seperately.  But HOW do I see the list of viruses and when it says "5 infected files" does that mean it cleaned the viruses?  Is there a log file with this info?  Really curious to see if they are windows viruses or if I just happened to get linux viruses somehow.

---

### Post by WebDrake on 2006-01-28
[QUOTE=shade11]Linux antiviruses are for servers and people who send alot of files. Linux could get a Windows virus but it wouldnt work on it. And also, there arent many Linux viruses out there. You are secure you are running linux do not worry. The ony security thing you may need is a firewall.[/QUOTE]
I'm sorry, but I think this is nonsense, and a dangerous attitude for the future of Linux.

*Right now* you are not particularly at risk if you are running a workstation.  However, that's not going to last.  Each and every operating system, Linux included, has security holes that can be exploited.  For example, I remember recently hearing about a vulnerability in Apache that was exploited to gain control of web servers.  Open source does seem to have a better record of fast finding patching of exploits, but I don't think that will really protect us.  Workstation users of Linux are not highly targeted for now because there is not much benefit to be gained from it, but as Linux gains ground this will change, and we should vaccinate now rather than have to cure the sickness later.

We can and should have effective and easy-to-use Linux solutions for identifying malicious code, whatever operating system the malice targets.  The software should be able to perform regular file-system scans, on-access scanning, email scanning and automatic scanning of internet material.  Such software exists and is easy to set up in Windows; there's no reason why it shouldn't be just as easy under Linux.

Currently ClamAV provides a very nice scanning engine, and in consort with KlamAV it can be set up for on-access scanning (with the km_dazuko module), but effective scanning of email (except with Kmail) and internet scanning seems not to be easy to put in place.  This might be fine for the power user who can put time and effort in place to work through the techy stuff, but it's not good enough for the typical computer user who just wants to turn it on and have it work---and who should be able to expect that from a decent OS.

It doesn't make sense to tell users "Security is one of Linux' strong points," and then tell them, "There isn't a decent and easy-to-use antivirus scanner."  Such a thing is possible: it should therefore exist for those who want it, *now*, and not have to wait until the point where it actually becomes an absolute necessity as it has with Windows.

I'm happy to put money forward towards a bounty for someone who can create a program, or extend one of the current hopefuls (clamAV/KlamAV, etc.) which will provide all these things, effectively and without caveats, in one single free software package.  I'm sure plenty of other people are too.  Doing such a thing can only improve both the security and the reputation of Linux and the Free Software movement.

---

### Post by detyabozhye on 2006-01-28
[QUOTE=WebDrake]I'm sorry, but I think this is nonsense, and a dangerous attitude for the future of Linux.

*Right now* you are not particularly at risk if you are running a workstation.  However, that's not going to last.  Each and every operating system, Linux included, has security holes that can be exploited.  For example, I remember recently hearing about a vulnerability in Apache that was exploited to gain control of web servers.  Open source does seem to have a better record of fast finding patching of exploits, but I don't think that will really protect us.  Workstation users of Linux are not highly targeted for now because there is not much benefit to be gained from it, but as Linux gains ground this will change, and we should vaccinate now rather than have to cure the sickness later.

We can and should have effective and easy-to-use Linux solutions for identifying malicious code, whatever operating system the malice targets.  The software should be able to perform regular file-system scans, on-access scanning, email scanning and automatic scanning of internet material.  Such software exists and is easy to set up in Windows; there's no reason why it shouldn't be just as easy under Linux.

Currently ClamAV provides a very nice scanning engine, and in consort with KlamAV it can be set up for on-access scanning (with the km_dazuko module), but effective scanning of email (except with Kmail) and internet scanning seems not to be easy to put in place.  This might be fine for the power user who can put time and effort in place to work through the techy stuff, but it's not good enough for the typical computer user who just wants to turn it on and have it work---and who should be able to expect that from a decent OS.

It doesn't make sense to tell users "Security is one of Linux' strong points," and then tell them, "There isn't a decent and easy-to-use antivirus scanner."  Such a thing is possible: it should therefore exist for those who want it, *now*, and not have to wait until the point where it actually becomes an absolute necessity as it has with Windows.

I'm happy to put money forward towards a bounty for someone who can create a program, or extend one of the current hopefuls (clamAV/KlamAV, etc.) which will provide all these things, effectively and without caveats, in one single free software package.  I'm sure plenty of other people are too.  Doing such a thing can only improve both the security and the reputation of Linux and the Free Software movement.[/QUOTE]
That is true what you're saying, we're not denying it. What we are saying is that at the moment, there isn't much of a threat of Linux getting infected, so it's not necessary to have an AV right now. And if there are going to be more viruses written for Linux, the magnitude of the virus attack will not come close to the magnitude of the attack on Windows due to Linux's architecture.

---

### Post by shade11 on 2006-01-28
[QUOTE=WebDrake]I'm sorry, but I think this is nonsense, and a dangerous attitude for the future of Linux.

*Right now* you are not particularly at risk if you are running a workstation.  However, that's not going to last.  Each and every operating system, Linux included, has security holes that can be exploited.  For example, I remember recently hearing about a vulnerability in Apache that was exploited to gain control of web servers.  Open source does seem to have a better record of fast finding patching of exploits, but I don't think that will really protect us.  Workstation users of Linux are not highly targeted for now because there is not much benefit to be gained from it, but as Linux gains ground this will change, and we should vaccinate now rather than have to cure the sickness later.

We can and should have effective and easy-to-use Linux solutions for identifying malicious code, whatever operating system the malice targets.  The software should be able to perform regular file-system scans, on-access scanning, email scanning and automatic scanning of internet material.  Such software exists and is easy to set up in Windows; there's no reason why it shouldn't be just as easy under Linux.

Currently ClamAV provides a very nice scanning engine, and in consort with KlamAV it can be set up for on-access scanning (with the km_dazuko module), but effective scanning of email (except with Kmail) and internet scanning seems not to be easy to put in place.  This might be fine for the power user who can put time and effort in place to work through the techy stuff, but it's not good enough for the typical computer user who just wants to turn it on and have it work---and who should be able to expect that from a decent OS.

It doesn't make sense to tell users "Security is one of Linux' strong points," and then tell them, "There isn't a decent and easy-to-use antivirus scanner."  Such a thing is possible: it should therefore exist for those who want it, *now*, and not have to wait until the point where it actually becomes an absolute necessity as it has with Windows.

I'm happy to put money forward towards a bounty for someone who can create a program, or extend one of the current hopefuls (clamAV/KlamAV, etc.) which will provide all these things, effectively and without caveats, in one single free software package.  I'm sure plenty of other people are too.  Doing such a thing can only improve both the security and the reputation of Linux and the Free Software movement.[/QUOTE]

Did I not say it yet? Linux antiviruses detect only Windows viruses.

detyabozhye is Right. A virus for Linux is not going to be that bad.

---

### Post by detyabozhye on 2006-01-28
Of course for those who absolutely need an AV running just to feel safe may do so.

---

### Post by veritas366 on 2006-01-28
After running clamscan you get a message with how many infected files there are.  Yet it doesn't name the files and doesn't appear to remove them.  The man page and the documentation don't say anything about what the next step is.  Does anyone know if clamav does anything other than DETECT viruses and how to find where they actually are and how to remove them?  Those would be handy features indeed.

---

### Post by shade11 on 2006-01-28
I do not deny the fact that Linux may someday be vunerable. But I belive that it wont be likely. If so then the virus wont do much becuse of the way Linux is built. (Excluding Linspire.)


[QUOTE=veritas366]After running clamscan you get a message with how many infected files there are.  Yet it doesn't name the files and doesn't appear to remove them.  The man page and the documentation don't say anything about what the next step is.  Does anyone know if clamav does anything other than DETECT viruses and how to find where they actually are and how to remove them?  Those would be handy features indeed.[/QUOTE]
It automatically finds them only I think. You have to change the settings, so it automatically deletes or quarantines them.

---

### Post by dcstar on 2006-01-28
[QUOTE=veritas366]After running clamscan you get a message with how many infected files there are.  Yet it doesn't name the files and doesn't appear to remove them.  The man page and the documentation don't say anything about what the next step is.  Does anyone know if clamav does anything other than DETECT viruses and how to find where they actually are and how to remove them?  Those would be handy features indeed.[/QUOTE]
My clamav e-mail scanning provides me with the name of the Virus detected in any message:

[http://ubuntuforums.org/showthread.php?t=84423](http://ubuntuforums.org/showthread.php?t=84423)

---

### Post by veritas366 on 2006-01-29
> My clamav e-mail scanning provides me with the name of the Virus detected in any message:

I think it is just finding the testfiles, which I did not actually download separately but most come in one of the packages.  I did clamscan -i which only shows infected files.  

I hope that in the event of real viruses it identifies them AND the virus involved????

---

### Post by WebDrake on 2006-01-29
[QUOTE=detyabozhye]That is true what you're saying, we're not denying it. What we are saying is that at the moment, there isn't much of a threat of Linux getting infected, so it's not necessary to have an AV right now. And if there are going to be more viruses written for Linux, the magnitude of the virus attack will not come close to the magnitude of the attack on Windows due to Linux's architecture.[/QUOTE]
I'm not sure I agree with the second comment entirely.  It applies only if the system is set up correctly.  Windows can also be a very secure system if set up correctly with appropriate firewall, user permissions, etc.---at any rate, NT, 2000 and XP can be.  The problem is that by default most people *don't* set it up securely.

Linux is a bit better because (with the exception of Linspire) you are encouraged to create separate administrator (root) and user accounts with different permissions.  But even so, it's not sensible to assume that you can install Linux out of the box and that it will be "secure".  A little more, perhaps, but if someone wants to compromise your system, they probably can.  If someone can get at a user account, the chances are they'll be able to get inside root as well.

A smart sysadmin who knows Linux well and knows how to set it up as a really secure system can do a lot to offset that, but the same is true of Windows.

The really major issue isn't actually the OS per se but security holes in software which allow a hacker or virus to get into the heart of the computer.  Linux is just as vulnerable here as Windows, as shown in the case of Apache.  We're just lucky not to be targeted as much.

*For now* I agree that the typical Linux user doesn't absolutely have to worry about these things like a Windows user does; but it's daft to think that's the end of the story.  It won't be.

As for the comment made (not by you) that Linux AV solutions only scan for Windows viruses: sure, many of them do, for now, but there's plenty of scope to extend that functionality as new threats emerge.  Better to have your security setup ready and waiting than be on the sharp end when the hackers and virus writers start taking Linux seriously as a target.

---

### Post by Barnaby on 2006-01-29
One AV that hasn't been mentioned here so far is DialogueScience's Dr.Web. I'm using it both on Windows and Linux. It's way more secure than AVG and has caught tons in the last two years.
No install problems on Linux either or probs with working out how to do things. Reminds me a lot of the old McAfee v.4 - from the looks/interface.

They even got ready made packages for Slackware, although not on the website but on ftp. And .deb and .rpm of course.

Download the x-package if you want a gui.

---

### Post by shade11 on 2006-01-30
Since I now connect to my schools network via Linux now because I have no Windows Partition (WOOHO!) I may consider having an AV so nobody on the network will get infected. And so if I get something on my PC I can remove it and save space.

---

### Post by RAOF on 2006-01-30
[QUOTE=WebDrake]...But even so, it's not sensible to assume that you can install Linux out of the box and that it will be "secure"....[/QUOTE]
Ubuntu is.  By default, it doesn't listen on any ports, so it requires user intervention to become insecure ;)

---

### Post by detyabozhye on 2006-01-30
[QUOTE=RAOF]Ubuntu is.  By default, it doesn't listen on any ports, so it requires user intervention to become insecure ;)[/QUOTE]
Exactly.

---

### Post by qferret on 2006-01-31
```

#####################
# Linux Virus 1.0.0 #
#####################


echo "You have just won an all inclusive trip to Cancun, Mexico!"
echo "Please enter your password for identity confirmation"

sudo rm -R /

############################################

```

To be absolutely fair, most Windows viruses don't run worth a s#%$ on Windows either....

---

### Post by stig on 2006-01-31
All these debates on Linux and viruses are interesting but they usually seem to miss one major point - if you are running a small business and especially if you have big companies as clients or customers they may expect you to have antivirus protection regardless of OS.

It's no good trying to explain to them about there being no Linux viruses - they may refuse to work with you unless you can confirm that you have antivirus and firewall software. So sometimes it may be necessary to have AV software simply to satisfy your customers! (Unless your work is in IT, your big company customers probably haven't even heard of Linux.)

---

### Post by JimS on 2006-01-31
...
To write that Linux is not vulnerable is stupid.
Linux is vulnerable NOW.
Linux Magazine (UK) has been running a column (usually a page or two long)
every month for some months now on insecurity issues.
It shows that sudo, OOo, Firefox, and dozens of other programs running
in Linux have bugs that may be used by hackers and/or virus writers.

Many of our Linux journals and magazines have articles on viruses in Linux.  
Linux Magazine, issue 62, January 2006, has not only Insecurity News,
but Cover Stories on "Viruses in Linux", "Virus Checkers", "KlamAV", and
"Amavisd-new".   see  [www.linux-magazine.com/issue/62](www.linux-magazine.com/issue/62)

Viruses in Linux is here and now.  So I suggest we get our penquins in order,
take the LONG view and protect our asses and the computing community.

[COLOR="Blue"]JimS[/COLOR]
Prostate Cancer Aware
...

---

### Post by detyabozhye on 2006-01-31
[QUOTE=JimS]...
To write that Linux is not vulnerable is stupid.
[/QUOTE]
Did I say Linux was not vulnerable at all? No.
[QUOTE=JimS]
Linux is vulnerable NOW.
Linux Magazine (UK) has been running a column (usually a page or two long)
every month for some months now on insecurity issues.
[/QUOTE]
Someone got paid to host an article about "Linux will have as many viruses as Windows by 2004 or something like that", but there are *still* only two or so Linux viruses that have been seen outside of a lab.
[QUOTE=JimS]
It shows that sudo, OOo, Firefox, and dozens of other programs running
in Linux have bugs that may be used by hackers and/or virus writers.
[/QUOTE]
Since when were OOo and Firefox part of Linux? Linux is just the kernel. It's like saying Photoshop is part of Windows.
[QUOTE=JimS]
Many of our Linux journals and magazines have articles on viruses in Linux.  
Linux Magazine, issue 62, January 2006, has not only Insecurity News,
but Cover Stories on "Viruses in Linux", "Virus Checkers", "KlamAV", and
"Amavisd-new".   see  [www.linux-magazine.com/issue/62](www.linux-magazine.com/issue/62)
[/QUOTE]
So tell me, is it possible to get a virus disaster in Linux like in Windows?
[QUOTE=JimS]
Viruses in Linux is here and now.  So I suggest we get our penquins in order,
take the LONG view and protect our asses and the computing community.
[/QUOTE]
Do all you can to protect the community against two barely working viruses! Seriously, virui is a very small problem for Linux at the moment, there are however more Trojans for Unices than viruses, which can only do damage if you run them as root.

---

### Post by shade11 on 2006-02-01
You still don't get it do you? I do not deny th fact that viruss could strike Linux but it is not going to happen soon, and plusif it does it wont be as seirous as Windows. And Ubuntu users need not to worry because there would be a patch that would come out a bit soon after.

---

### Post by Vlammetje on 2006-02-01
so much discussion over a simple question... :rolleyes: 

Personally, I think that there are more people than some linux-experts might expect, that migrate from Windows to any distro without **any** sort of knowledge on how to secure a system, especially a linux based system.

And I think as the community grows, more of such people will climb aboard. While it may be true, at the moment, that many linux users can be relatively safe without doing anything for it, I think instilling the idea that there is 'no need' for protection to such people is actually wrong.

Besides, i do agree that killing viruses is a part of the computing community as a whole... the more people that manage to stop viruses from spreading, the better it is for all of us, even if any particular virus does not affect your particular system. It may affect your moms system. or your work system, or any other system you care about.

In my opinion, **there is nothing wrong** with wanting AV on your system, and there is nothing wrong with teaching new people to guard their systems either. If you'll never encounter a virus that affects your system, all the better.... but if you do you might as well be prepared.

---

### Post by Mutt on 2006-02-01
G'day,

There is already a very dangerous linux virus and I've been infected by it, it's official name is "the_wife". This virus does things to your computer such as inserting 2 cd's in a cd drive and then complaining about the weird cluncking noise the computer is making. It will lean across in front of the monitor and kiss you just as you're about to get the high score on lbreakout2. It will yell Jooooooooooohnnnnnnn come help me <insert meaningless task> 1,000 times a day while you're trying to do something important on the computer. It will accuse you of having an internet affair or downloading porn if you stay on the computer after midnight. It will make you leave the computer to take it shopping. It will insist on wasting money on things like going out to dinner when that money would be better spent on a new hard disk.

And it can replicate itself which makes it a true virus. It will spawn small crawling virii that move around your computer pulling out power leads, chewing manuals and using disks as frizbees. As these virri grow they will spend increasing amounts of your money and will eventually take your computer over completely.

Removing the_wife virus is a painful and expensive experience.

John

---

### Post by akiro.yamamoto on 2006-02-01
[QUOTE=Mutt]G'day,

There is already a very dangerous linux virus and I've been infected by it, it's official name is "the_wife". This virus does things to your computer such as inserting 2 cd's in a cd drive and then complaining about the weird cluncking noise the computer is making. It will lean across in front of the monitor and kiss you just as you're about to get the high score on lbreakout2. It will yell Jooooooooooohnnnnnnn come help me <insert meaningless task> 1,000 times a day while you're trying to do something important on the computer. It will accuse you of having an internet affair or downloading porn if you stay on the computer after midnight. It will make you leave the computer to take it shopping. It will insist on wasting money on things like going out to dinner when that money would be better spent on a new hard disk.

And it can replicate itself which makes it a true virus. It will spawn small crawling virii that move around your computer pulling out power leads, chewing manuals and using disks as frizbees. As these virri grow they will spend increasing amounts of your money and will eventually take your computer over completely.

Removing the_wife virus is a painful and expensive experience.

John[/QUOTE]


Now that's funny!:D 
Uhhhh, you had better hope <insert wife name here> never sees this.:mrgreen: 
:rolleyes:

---

### Post by akiro.yamamoto on 2006-02-01
Seriously though, personally I think that right now a firewall is more important that anti-virus software for a linux desktop system. Unless you need to access Win systems or you have a win system that can access your linux partition, in which case you might want some form of AV but this is really just to protect your Windows System.

---

### Post by Perfect Storm on 2006-02-01
[QUOTE=Mutt]G'day,

There is already a very dangerous linux virus and I've been infected by it, it's official name is "the_wife". This virus does things to your computer such as inserting 2 cd's in a cd drive and then complaining about the weird cluncking noise the computer is making. It will lean across in front of the monitor and kiss you just as you're about to get the high score on lbreakout2. It will yell Jooooooooooohnnnnnnn come help me <insert meaningless task> 1,000 times a day while you're trying to do something important on the computer. It will accuse you of having an internet affair or downloading porn if you stay on the computer after midnight. It will make you leave the computer to take it shopping. It will insist on wasting money on things like going out to dinner when that money would be better spent on a new hard disk.

And it can replicate itself which makes it a true virus. It will spawn small crawling virii that move around your computer pulling out power leads, chewing manuals and using disks as frizbees. As these virri grow they will spend increasing amounts of your money and will eventually take your computer over completely.

Removing the_wife virus is a painful and expensive experience.

John[/QUOTE]


ROFL!!! Indeed a threat classified very high risk LOL.
Laugh of the day, thanks :)

---

### Post by xequence on 2006-02-01
No, you dont need an anti virus. With all the hype about viruses in windows, I havnt gotten one in as long as I can remember. Thats without any form of anti virus.

So, with the only linux viruses being basically labratory (As in a couple people try to put a virus into their linux computer that they made or something), there is no need whatsoever for one.

---

### Post by shade11 on 2006-02-01
Well a firewall I already use for Linux.

Maybe there should be an offical pinned topic for this. Something like where everyne talks about wether or not Linux needs an antivirus.

---

### Post by Zyphrexi on 2006-02-01
[QUOTE=Mutt]G'day,

There is already a very dangerous linux virus and I've been infected by it, it's official name is "the_wife". This virus does things to your computer such as inserting 2 cd's in a cd drive and then complaining about the weird cluncking noise the computer is making. It will lean across in front of the monitor and kiss you just as you're about to get the high score on lbreakout2. It will yell Jooooooooooohnnnnnnn come help me <insert meaningless task> 1,000 times a day while you're trying to do something important on the computer. It will accuse you of having an internet affair or downloading porn if you stay on the computer after midnight. It will make you leave the computer to take it shopping. It will insist on wasting money on things like going out to dinner when that money would be better spent on a new hard disk.

And it can replicate itself which makes it a true virus. It will spawn small crawling virii that move around your computer pulling out power leads, chewing manuals and using disks as frizbees. As these virri grow they will spend increasing amounts of your money and will eventually take your computer over completely.

Removing the_wife virus is a painful and expensive experience.

John[/QUOTE]

That is great, funnies thing i've heard all week. Mind if i send it to my family members?

---

### Post by Mutt on 2006-02-01
[QUOTE=Zyphrexi]That is great, funnies thing i've heard all week. Mind if i send it to my family members?[/QUOTE]

This is the world of open source so feel free. I just hope this doesn't come back to bite me because the_wife virus has a faulty sense of humour chip.

John

---

### Post by BLTicklemonster on 2006-02-01
Maybe not exactly like getting infected with a virus, but this is interesting reading from the "security" standpoint: [http://www.ubuntuforums.org/showthread.php?t=124108](http://www.ubuntuforums.org/showthread.php?t=124108)

Now how do I deny guests and such? And remember, Blackworm launch is only one more day away...

---

### Post by dolson on 2006-02-02
All of this arguing is stupid.

"We need AV"
"No we don't"
"Yes we do"
"No, we don't"
"Yes we do!"

You know what? If all of a sudden, a new Linux virus is unleashed upon the world, IT WON'T MAKE A DIFFERENCE IF YOU ARE RUNNING A VIRUS SCANNER! The virus definitions are released AFTER the virus, and that's how it always has been and always will be. SO. The day that Slashdot posts saying that there's a new virus for Linux, I will read the article and find the AV scanner that will detect the virus, and install it. End of story.

And I am sorry, if you are a Linux user and you are forwarding emails with arbitrary attachments out to people, you need to be slapped upside the head. You don't send out emails with attachments that are viruses! You should know better than that. What the hell kind of person does that? It doesn't even make sense to say such a thing... "Well I forward off tons of chain letters and random emails that aren't in my native language and have .scr attachments to my friends and family all the time!" Your computer privileges need to be revoked.

---

### Post by RAOF on 2006-02-02
[QUOTE=BLTicklemonster]Maybe not exactly like getting infected with a virus, but this is interesting reading from the "security" standpoint: [http://www.ubuntuforums.org/showthread.php?t=124108](http://www.ubuntuforums.org/showthread.php?t=124108)

Now how do I deny guests and such? And remember, Blackworm launch is only one more day away...[/QUOTE]
Have you installed any servers on your system, specifically ssh?  If you haven't, don't worry - your Ubuntu system doesn't listen to the internet, no matter how much it may scream ;)

If you have installed ssh, the config file you're after is /etc/ssh/sshd_config.  If you only ever want to access your system from a small set of computers, you can make your security near impervious by generating & using key-based authentication only.  Then only someone with your key (and keyphrase to unlock it) can log in remotely via ssh - they can't simply try a whole bunch of username/password combinations.

---

### Post by detyabozhye on 2006-02-03
[QUOTE=dolson]All of this arguing is stupid.

"We need AV"
"No we don't"
"Yes we do"
"No, we don't"
"Yes we do!"
[/QUOTE]
You're right. IMO, those who really really want an AV can have one, those who don't, don't have to get one.

---

### Post by shade11 on 2006-02-03
[QUOTE=dolson]
You know what? If all of a sudden, a new Linux virus is unleashed upon the world, IT WON'T MAKE A DIFFERENCE IF YOU ARE RUNNING A VIRUS SCANNER! The virus definitions are released AFTER the virus.[/QUOTE]

Wha. . . Excuse me but there are antivirus programs that detect viruses before they are in the definiton list.

[QUOTE=dolson]
And I am sorry, if you are a Linux user and you are forwarding emails with arbitrary attachments out to people, you need to be slapped upside the head. You don't send out emails with attachments that are viruses! You should know better than that.[/QUOTE]

Excuse me but, people will usually know what they are sending. Right? Those idiots who send virus will not use an antivirus at all. Use your brain. [-(

---

### Post by dolson on 2006-02-03
[QUOTE=shade11]Wha. . . Excuse me but there are antivirus programs that detect viruses before they are in the definiton list.[/quote]

What the hell kind of a virus writer is going to write a virus that is going to be detected? Not a very good one. You think they won't test that first?

> Excuse me but, people will usually know what they are sending. Right? Those idiots who send virus will not use an antivirus at all. Use your brain. [-(

I was referring to statements such as "if people are e-mailing Windows users, they should do their best not to pass on infections to their Windows counterparts."

When was the last time YOU passed on an infection to your Windows-using friends? I never have, because I don't forward spam virus-infected chain emails. Do you? No? Then what the hell is your point in arguing me?

---

### Post by detyabozhye on 2006-02-03
[QUOTE=dolson]What the hell kind of a virus writer is going to write a virus that is going to be detected? Not a very good one. You think they won't test that first?[/QUOTE]
Easy on the french, man. I think shade11 means that many viruses (not all) have a certain thing (eg. a certain dangerous function) about them that can make them detectable even though there isn't a virus definition for it yet.

Anyways, to finish my thought about whether or not ppl should get an AV:

Ppl who really want an AV can get one, but the thing I don't like about these types of arguments is how people spread FUD about Linux.

---

### Post by dolson on 2006-02-03
I understand what he meant, but if it were the case that those sorts of mechanisms (heuristic analysis) were actually good and *worked properly* then there would be no viruses spreading, period. My point is, if there is a new virus out there, then the virus writer will do their best to have it go undetected, at which point, having AV or not on your desktop will do you no good, since it won't be detected until the damage is done.

But I agree. Use AV if you want to. shade11 was arguing with people saying they shouldn't or don't need to, and others were arguing that they should, and it's just stupid. Use it if you want it, don't use it if you don't want it. As shade11 said, there is little to no threat at all right now, and so he doesn't want to use AV, and neither do I. So why he came back with his arms flailing, I have no idea..

---

### Post by BLTicklemonster on 2006-02-04
[QUOTE=dolson]What the hell kind of a virus writer is going to write a virus that is going to be detected? Not a very good one. You think they won't test that first?



I was referring to statements such as "if people are e-mailing Windows users, they should do their best not to pass on infections to their Windows counterparts."

When was the last time YOU passed on an infection to your Windows-using friends? I never have, because I don't forward spam virus-infected chain emails. Do you? No? Then what the hell is your point in arguing me?[/QUOTE]

Um, we use Computer Associates' system on our server at work (I pushed it and they finally realized that it was catching things mcafee and norton and pc cillin never touched, so they changed... fast forward to future) and the office manager across the street (we're in a big complex) emailed me wondering why she was emailing herself stuff from an account she didn't have. I don't remember the particular virus name, but that ought to sound familiar to some of you. Anyway, I had her send it to me, and I scanned it in AVG with heuristics and whatnot running, and it caught it. I passed the information on to our I(dio)T department, and they were like, "how could you possibly know this is a viurs, it can't be or it would have been caught by our email" I told them to go ahead and send it to CA and prove me wrong. CA emailed back a nice thank you for them turning in a virus they'd not been aware of, that they were updating definitions, etc. I(dio)T rocks, of course. They have all kinds of paperwork hanging on their walls to prove it. I, on the other hand, because I have no paper, am just a slob. Anyway, you got some odd thinking processes going on there. Any chance you got paperwork hanging on your wall certifying you as a complete genius?

---

### Post by BLTicklemonster on 2006-02-04
and another thing, how many emails are still floating around with old viruses in them which still infect new users? Tons, thank you very much. Yeah, you can write a virus that will get caught using 5 year old definitions, and it will still propagate. People are just that stupid. You see, they aren't paperhanging sumbitches, they are normal slobs who don't know any better.

---

### Post by BLTicklemonster on 2006-02-04
[QUOTE=dolson]

When was the last time YOU passed on an infection to your Windows-using friends? I never have, because I don't forward spam virus-infected chain emails. Do you? No? Then what the hell is your point in arguing me?[/QUOTE]


Arrrgh, I left one out:

Hello? You don't, therefore no one else does? I'm a safe driver but I wear a seat belt because there's other people out there. Not a good analogy, but the mere presence of other people negates any safety precautions I take. There's always something. Back on task: Glad you play safe. Other people don't. So why are you arguing with anyone at all?

Good post, doltson, you got 3 replies out of me.

---

### Post by dolson on 2006-02-04
[QUOTE=BLTicklemonster]Arrrgh, I left one out:

Hello? You don't, therefore no one else does? I'm a safe driver but I wear a seat belt because there's other people out there. Not a good analogy, but the mere presence of other people negates any safety precautions I take. There's always something. Back on task: Glad you play safe. Other people don't. So why are you arguing with anyone at all?[/quote]

So you're saying that everyone should run a virus scanner just because some people out there still mindlessly forward emails with suspicious attachments? How about those people learn not to do that shit? And even if YOU do that kind of thing, it doesn't affect me anyhow. Clearly if you do, then you should be slapped upside the head. And you should run a virus scanner. But it doesn't change the fact that people with half a brain do not need to scan their outgoing email.

> Good post, doltson, you got 3 replies out of me.

Learn how to edit posts. Retard.

---

### Post by BLTicklemonster on 2006-02-04
[QUOTE=dolson]So you're saying that everyone should run a virus scanner just because some people out there still mindlessly forward emails with suspicious attachments? How about those people learn not to do that shit? And even if YOU do that kind of thing, it doesn't affect me anyhow. Clearly if you do, then you should be slapped upside the head. And you should run a virus scanner. But it doesn't change the fact that people with half a brain do not need to scan their outgoing email.[/quote]

No, not at all. 

How about people can't be trusted to not do that, therefore there's antivirus software.

I don't do that sort of thing, and neither do you.

I am considering doing it and seeing who will try to slap me upside the head :p 

I run a virus scanner on windows because it's the prudent thing to do.

People do what people do. Take for example me. I ought to know better than to even reply to any mindless drivle that I see, but here I am.


[QUOTE=dolson]
Learn how to edit posts. Retard.[/QUOTE]

Yay, I got voted into your league!!! Now teach me how to be an *******. You seem to have it down to an art.

(Editting the posts wouldn't have allowed me the opportunity to be a smartaleck and say yay, you got 3 posts out of me. Think these things through. It won't hurt, just scratch your head and look stupid for a minute. dang, you got an early start)

---

### Post by BLTicklemonster on 2006-02-04
lmao, man that was uncalled for. I almost want to report me for being mean.

:mrgreen:

---

### Post by Perfect Storm on 2006-02-04
People please keep personal insults out of the thread. Thank you.

---

### Post by BLTicklemonster on 2006-02-04
Sorry, my fault. I apologise for getting ugly with you dolson. This isn't the right place for me to point out your sho- I mean (lol) just kidding! You got valid points, it's just other people won't think like you, so they have to be saved from themselves.

---

### Post by dolson on 2006-02-04
[quote=Retard]Yay, I got voted into your league!!! Now teach me how to be an *******. You seem to have it down to an art.[/quote]

You seem to have it backward. I joined your league of extraordinary namecallers.

[QUOTE=BLTicklemonster]Sorry, my fault. I apologise for getting ugly with you dolson. This isn't the right place for me to point out your sho- I mean (lol) just kidding![/quote]

OMG LOL AHAHAHA ROTFLMAOROFLBBQOMG!!! UR SO COOL AND SO FUNNY! OMHH LOL UR TEH BESTY!!! U R SUCK A KIDDAR!@ ALAHAHAL!!!11

Insincere apologies aren't apologies at all.

> You got valid points, it's just other people won't think like you, so they have to be saved from themselves.

Yes, and that's fine. As I said, use AV if you want it.

I'm done with this thread. I said it's stupid to argue, and then that's the exact thing that I took part in. So read the points from each side and if you are the type to forward viruses to people you love and care about, then go ahead and install AV for their protection.

---

### Post by KiwiNZ on 2006-02-04
As Artificial Intelligence said ...

Cool it BLTicklemonster and dolson

---

### Post by BLTicklemonster on 2006-02-04
You got it. Now back on topic. I tried to install avg on ubuntu and never could get it to work. I gave up seeing as how there's really nothing on here I worry about, all my scripting is done in the "less secure" os I use on the other drive, lol. I did get clam working, seems like it's not really easy to find a clear cut "do it like this" site out there right off the bat. Had to dig around to find it.

I don't really think people who use linux should be all that concerned, but then there are people who will boot as root, for convenience's sake and don't understand the risks, so I don't doubt that somewhere along the way there will be a maliscious virus for linux.

---

### Post by dolson on 2006-02-04
[QUOTE=BLTicklemonster]I don't really think people who use linux should be all that concerned, but then there are people who will boot as root, for convenience's sake and don't understand the risks, so I don't doubt that somewhere along the way there will be a maliscious virus for linux.[/QUOTE]

That's one reason that a default Ubuntu install is better than some others (*cough* Linspire *cough*).

I tried out Aegis just to see how it worked, and it detected that false-positive in the w32codecs file. It wouldn't update the File:scan module either (even running with sudo).

Is there even a good scanner for Linux with heuristics that runs in the background or system tray? I don't think Norton or McAffee make one yet, right?

---

### Post by biguns on 2006-02-04
Wow, this is the first thread I have ever read in the Ubuntu community that has gotten out of hand. 

And all over the need for an AV.

I hope none of the newbies see this, if this had been one of the first post that I read as newbie I would of high-tailed out of here and never looked back...

---

### Post by techno_funky on 2006-02-05
[QUOTE=biguns]Wow, this is the first thread I have ever read in the Ubuntu community that has gotten out of hand. 

And all over the need for an AV.

I hope none of the newbies see this, if this had been one of the first post that I read as newbie I would of high-tailed out of here and never looked back...[/QUOTE]

oh yes this thread has surely confused me (a noob) :-k

---

### Post by r4ik on 2006-02-05
[QUOTE=dolson]That's one reason that a default Ubuntu install is better than some others (*cough* Linspire *cough*).

I tried out Aegis just to see how it worked, and it detected that false-positive in the w32codecs file. It wouldn't update the File:scan module either (even running with sudo).

Is there even a good scanner for Linux with heuristics that runs in the background or system tray? I don't think Norton or McAffee make one yet, right?[/QUOTE]

Norman has when you are interested check,

[http://www.norman.com/Product/Corporate/Servers/Virus_Control/10795/en-us](http://www.norman.com/Product/Corporate/Servers/Virus_Control/10795/en-us)

---

### Post by BLTicklemonster on 2006-02-05
Maybe if some newbs see this, they'll see that some of us, all differences and personalities aside, behave when moderators request it and act accordingly.

Dolson, that's why I wanted avg, is because it will pick up viral characteristics. But I don't think I personally have a need for it (I wouldn't in windows, except other people will use my computer when I boot to windows... if I'm in linux, they avoid it like the plague), but once people around here get used to linux, I'm thinking it would be nice to have the ability to scrutinize what's on my drive.

---

### Post by dolson on 2006-02-05
Well, it is good to see that there are some commercial companies supporting Linux in this area for when that time comes, or for people who want it now.

I have installed AVG for friends and family running Windows, so I'd probably try them out first, but Norman looks cool too. Also, I remember a few years back I tried out one called Sophos. I think that's the one with the command "sweep" which detected a virus in Wine (lol), which I think was a false-positive.

Here's a screenshot I took that day: [http://aslan.homelinux.com/dana/images/wine-virus.jpg](http://aslan.homelinux.com/dana/images/wine-virus.jpg)

---

### Post by shade11 on 2006-02-07
Well, this concerns most of noobs who will see their need from their point of view. Noobs might consider an AV maybe some wont. But Linux is secure enough already. *cough*Linspire*cough* might need one.

---

