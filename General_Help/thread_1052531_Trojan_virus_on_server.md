---
title: "Trojan virus on server"
date: 2009-01-27
forum: General Help
---

### Post by jkd03d on 2009-01-27
I was hoping that someone out there might be able to help me.  I am a linux newbe and can't seem to get this trojan virus off my ubuntu server.

The trojan virus seems to keep replicating.

I installed clamav and performed the following command: "clamscan --remove -r /"

The scan ran and found 30 trojan viruses.  ClamAV was not able to remove 3 of the 30 viruses.  Does anyone have any idea how I can remove all viruses from my server?

---

### Post by dcstar on 2009-01-27
> **jkd03d said:**
> I was hoping that someone out there might be able to help me.  I am a linux newbe and can't seem to get this trojan virus off my ubuntu server.

The trojan virus seems to keep replicating.

I installed clamav and performed the following command: "clamscan --remove -r /"

The scan ran and found 30 trojan viruses.  ClamAV was not able to remove 3 of the 30 viruses.  Does anyone have any idea how I can remove all viruses from my server?

What "virus" exactly are you referring to?

---

### Post by jkd03d on 2009-01-28
The name of the file is Trojan root-kit.

I am connecting to the server via SSH.  The virus seems to take down the network after the server has been up for about 10 mins.  I tried running clamav and used the move command (tried to move the viruses in a directory).  It seems like the viruses keep populating though.

Any ideas on how I can fix this?

---

### Post by UbuntuNerd on 2009-01-28
check this link out
[http://packages.ubuntu.com/hardy/chkrootkit]("http://packages.ubuntu.com/hardy/chkrootkit")

---

### Post by Gramps on 2009-01-28
I would try booting off a Live-CD and then try and run the anti-virus program, you maybe able to find one on a Live-CD.

At times I have had to use several different anti-virus programs to get rid of all traces of a virus.

You may also need to use a root-kit remover. Do a Google search for the one that is on your system to see how to get rid of it.

---

### Post by cariboo on 2009-01-28
It sounds like you've been cracked. THe best thing to do is to go to the server and pyhsically disconnect if from the internet. Boot from the LiveCD ,reconnect the network cable, install rkhunter and run it. 

The second best way is to removed the cracked hard drive, insert a new one and reinstall. Then review the security methods you had in place, as they obviously don't work.

Jim

---

### Post by jerome1232 on 2009-01-28
Correct me if I'm wrong but if you suspect your server has been rooted a clean install is the only way to go. . 

You might want to find out how your server was compromised in the first place, and revise your security policy. Root kits are nasty and some are undetectable from within the running OS that's been rooted.

---

### Post by jkd03d on 2009-01-28
I agree...I never really setup any security in the first place (hence why I have a virus).  

I used clonzilla to create an image before opening to the internet...so I will just reimage.

Does anyone know of any good howto docs relating to securing an ubuntu server?

Thanks for the help on this topic!

---

### Post by SOULRiDER on 2009-01-28
Check out [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by mb_webguy on 2009-01-28
Network security is as much an art as a science.  Crackers are very creative about finding new ways into sytems, and admins are always trying to stay one step ahead.  The first thing you should do is to keep your system updated (which is easy enough if you're using a good distribution with well-maintained repositories.  Beyond that, it's a matter of education, preparation, and prevention.  Here are a few links to get you started.

[Security on Ubuntu]("http://www.psychocats.net/ubuntu/security")
[Linux Server and Network Security]("http://www.aboutdebian.com/security.htm")
[Tips on basic Linux server security]("http://www.net-security.org/article.php?id=109")
[Linux Network Security]("http://www.sjdjweis.com/linux/security/")
[Linux Administrator's Security Guide - Linux Network Security]("http://www.linuxtopia.org/online_books/linux_administrators_security_guide/13_Linux_Network_Security.html")

---

### Post by albinootje on 2009-01-28
> **jkd03d said:**
> I agree...I never really setup any security in the first place (hence why I have a virus).  

I used clonzilla to create an image before opening to the internet...so I will just reimage.

Does anyone know of any good howto docs relating to securing an ubuntu server?

Thanks for the help on this topic!

So you're claiming that your server was "owned" after 10 minutes of Internet access ?
I find that a bit hard to believe, but if it's true, then it gets interesting..

Which Ubuntu release were you using ?
And did you apply all upgrades before putting your server online ?
Did you run a firewall ?
What services were you running ? (e.g. apache,ssh,ftp)
Did you use strong passwords ?

Can you run "rkhunter" and "chkrootkit" from a live cd scanning your hard disk ?

---

### Post by jrusso2 on 2009-01-28
If you don't lock it down you will be rooted again their are automated scripts that run just to crack insecure Linux servers, esp ssh.

---

### Post by albinootje on 2009-01-28
> **jkd03d said:**
>  The scan ran and found 30 trojan viruses.

And for being a good example towards others, let's not talk so superficial about viruses and trojans as the mass media often does.

A virus can infect your system through the user interaction, some viruses for Linux do exist, but it's unlikely that they can survive and spread for long.
The trojan horse looks like a good thing, which will turn out bad, again userinteraction is needed.
A worm is something which can enter your server without user interaction.
A brute-force attack can be used to break in when your user(s) have bad paswords.
A rootkit is installed after your system is compromised.

So.. if your machine is indeed compromised, then it's other a worm, or a brute-force attack, or a remote exploit (known or wild), or something else, BUT not a virus (unless you download untrusted 3rd party software, and compiled it etc.etc. which would be a trojan horse).

I would be surprised that clamav would give so many false positives, but it could be possible.

---

### Post by Dustin2128 on 2009-01-28
not really relating to the subject at hand, but do I have any risk of such intrusions (by that, I mean what's the level of probability) as a desktop user? I don't exactly think that hackers would target my system though.
Oh, rootkits after compromisation! Well how about those other attacks? I agree that clamav must be giving false positives though, because only about 40 viruses have ever existed for the linux platform, most in labs.

---

### Post by jerome1232 on 2009-01-28
> **Dustin2128 said:**
> not really relating to the subject at hand, but do I have any risk of such intrusions (by that, I mean what's the level of probability) as a desktop user? I don't exactly think that hackers would target my system though.
Oh, rootkits after compromisation! Well how about those other attacks? I agree that clamav must be giving false positives though, because only about 40 viruses have ever existed for the linux platform, most in labs.

As was mentioned before once a system is severely compromised a rootkit can be installed by the attacker, it is something that hides evidence that the system was compromised and keeps a backdoor open so the attacker can regain access to the system.

If your not running any servers on your desktop computer then there's really nothing there to exploit. You would have to download a trojan of some sort that contains a rootkit. Then run and install said rootkit yourself.

---

### Post by mb_webguy on 2009-01-28
To add to Jerome's post, if you're using a router you're even safer, since any cracker would have to get through it before attempting to crack your computer.  Most home users are very safe running Linux.

---

