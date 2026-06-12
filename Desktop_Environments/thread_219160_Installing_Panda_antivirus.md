---
title: "Installing Panda antivirus"
date: 2006-07-19
forum: Desktop Environments
---

### Post by Zingomoos135 on 2006-07-19
I fot this month's PC world (yay!) and it had a LOT of information about different PC security risks. It had mentioned that Linux is becoming exposed to certain types of viruses and suggested downloading panda antivirus.

i don't know how to install it. 

the archived package came with a folder entitled "opt" full of folders that have the same names of folder in the / filesystem.so i started just... moving them into the file system. but i think that's probably not the right move to make. 

how do i install panda antivirus? isn't there some way i can use the package manager to help??

thanks!

---

### Post by reacocard on 2006-07-19
there's probaly a README or INSTALLING file in it. follow the instructions it has.
EDIT: just looked at the site. which did you download? the rpm or the tar.gz ? if it was the rpm you'll need to use a program called alien to install it.

---

### Post by T700 on 2006-07-19
Please, do a search on this forum.  Read objective sources--not magazines trying to shill software for their advertisers.  Antivirus software is not necessary on Linux unless you are running a mailserver.  Then it is only needed to prevent virus laden emails from being passed to Windows users.

The structure of Linux just doesn't allow for the same type of attacks you see in the Windows world.  There are rootkits and the like, but viruses are not a concern.  Keep your system patched, run a firewall or NAT enabled router, don't install software from shifty sources, and you'll be fine.  I have run Windows since almost day one and am a paranoid, security freak who runs multiple antivirus and malware detectors on both mine and my client's machines.  I've run Linux since 1999 and have never felt the need for similar on any desktop system.

Paul

---

### Post by GTvulse on 2006-07-19
First off, PC World stopped being a credible trade magazine in the early 90's. Second, in general, such affirmations are mere marketing by FUD preying on people who do not know the truth: POSIX operating systems are not vulnerable to MS Windows-style computer virii. That doesn't mean that a GNU/Linux system is invulnerable to attack and penetration; it means that the methods and vulnerabilities are different. In general, most cracked GNU/LInux systems are so, because of administrative mistakes, be it human error when configuring a server, failure to patch the system with the security updates when they come out, or giving out the root passord at parties to impress chicks.

Because of the architectural design of the POSIX operating systems, it is almost impossible to have a normal user execute a binary program that escalates to administrative privileges and destroy the whole operating system, as it commonly happens in that other operating system.

The truth is, you see, the antivirii industry is worth tens of thousands of millions of devaluated but mighty US dollars. Now that Microsoft has moved into the antivirus business to get a cut in the racket, the antivirus companies are trying to move after the milking cows that have already moved on to use alternative operating systems such as GNU/Linux running away of the real virus threats in the MS products.

---

### Post by Zingomoos135 on 2006-07-19
haha that's kinda funny 'cause the only reason i chose to run Ubuntu instead of SuSe or someother form of linux was because pcworld had suggested it.

but on the subject of firewalls, are all linux firewalls text based, like running from terminal, or are there graphic interfaced firewalls for linux as well?

---

### Post by T700 on 2006-07-19
For a nice, graphic firewall:

```
gksudo firestarter
``` 
and press Enter.

Paul

---

### Post by Zingomoos135 on 2006-07-19
will i need to download a package first? or was it downloaded by default when i upgraded to ubuntu 6.06?

---

### Post by T700 on 2006-07-19
> **Zingomoos135 said:**
> will i need to download a package first? or was it downloaded by default when i upgraded to ubuntu 6.06?

Try it and see! :smile:

Paul

---

### Post by Zingomoos135 on 2006-07-19
i see a lot of conversation about Automatix, and you have a link in your signature. what is that?

---

### Post by Zingomoos135 on 2006-07-19
and is there really any configuring to do with firestarter other than just setting it up with the wizard? i know i can add rules to allow any IP addresses if i need to, but other than that, will it just run on its own?

---

### Post by T700 on 2006-07-19
> **Zingomoos135 said:**
> i see a lot of conversation about Automatix, and you have a link in your signature. what is that?

If you click on that link, it will take you to a page with a full, simple, explanation.

Paul

---

### Post by Delkster on 2006-07-19
> **dradul said:**
> Because of the architectural design of the POSIX operating systems, it is almost impossible to have a normal user execute a binary program that escalates to administrative privileges and destroy the whole operating system, as it commonly happens in that other operating system.

Virii and malware can spread without root privileges, although infecting program files is of course trickier if there's no write access to any of them.

There are very few virii for Linux (and, I suppose, none really in the wild at the moment), and I wouldn't bother with an anti-virus program at this time either, but I don't think it's entirely correct that Linux would be 'architecturally' or otherwise inherently immune to any kinds of malware, although things like the MSBlast worm epidemy are unlikely on Linux (and becoming more so on Windows as well now that there's at least some kind of firewall protection by default).

Most current anti-virus solutions available for Linux aren't very suitable for the desktop anyway.

---

### Post by nu2this on 2006-07-19
If u go to synaptic ClamWin AV is in there it's just as good & all you have to do there is to mark it for installation,click apply,done!

---

### Post by T700 on 2006-07-19
> **Delkster said:**
> Virii and malware can spread without root privileges, although infecting program files is of course trickier if there's no write access to any of them.

How?  

Paul

---

### Post by Delkster on 2006-07-19
> **T700 said:**
> How?

I have to admit that I'm not very familiar with the current trends in malware, most of all namely because it's had little effect on my personal computing in the past years.

However, malware can spread directly over the network. Virii have mass-posted themselves via e-mail, and worms may spread directly through socket connections. It doesn't take root privileges to open network connections or to sniff out addresses from a personal address book residing in the home directory.

Granted, as I said, by default Ubuntu doesn't listen to any ports outside of localhost, but some user applications may also open ports for listening (peer-to-peer filesharing comes to mind, and VoIP and instant messaging software sometimes do it as well) so vulnerabilities in such software could be exploited to distribute malware.

Similarly, being careful with e-mail reduces the risk, but that's so obvious that it's hardly worth mentioning. Of course being more careful in certain activities lowers the risk of infection, and that's well-known also in the Windows world.

---

### Post by GTvulse on 2006-07-19
[quote=Delkster]There are very few virii for Linux (and, I suppose, none really in the wild at the moment), and I wouldn't bother with an anti-virus program at this time either, but I don't think it's entirely correct that Linux would be 'architecturally' or otherwise inherently immune to any kinds of malware, although things like the MSBlast worm epidemy are unlikely on Linux (and becoming more so on Windows as well now that there's at least some kind of firewall protection by default).[/quote]

Believe it or not, the basic difference is architectural. POSIX systems are designed to restrict process execution and file access privileges. You may argue that the basic security model is "primitive" and that is correct in the sense that it is simple and old. The really important thing is that it *works* and works well, else it would have been replaced a long time ago. There have been additions, from filesystem and process accounting (that sets quotas on disk space, CPU time and system load) to highly sophisticated access control systems such as SELinux, AppArmor and others. In a single user desktop workstation, even in many multi-user server setups, they are overkill.

Your presumption that malware can act and behave as it does in Win32 systems is based on the widespread belief that applications in POSIX systems have the same kind of unnecesary system-level integration that those OSs have. Nothing further away from the truth. The *architecture* is completely different (yes, the *architecture*). In POSIX systems, processes are in principle isolated, and use well-defined user-space mechanisms to communicate with each other, protocols such as IPC, RPC, CORBA, etc. No application will execute code of another application gratitously as can, and will, happen with win32 OSs; the kernel, only arbitrates the information exchange, it doesn't have the ability to run it as an executable program; there are no system-wide scripting languages that have implicit rOOt privileges, such as the visual basic script ActiveX thingy. You cannot transfer knowledge from one reality domain to a different and completely alien one and expect it to work. 

I am not, under no curcumstance, making the affirmation that POSIX systems are invulnerable. You somehow managed to misquote me and implicitly suggest that I said exactly the contrary of what I just repeated in the previous sentence. No, what I said is that vulnerabilities and the methods of attack are very different. You did say corrrectly that the problems are related to opening network services using software with known vulnerabities.

Furthermore, in what pertains to firewalls, running something like Firestarter is simply a placebo. It fulfills no purpose other than having a log of purported attacks. Why would you want a software firewall when these days most people are behind a router with NAT/P and the routers themselves can act as true hardware firewalls? I agree that a Windows machine needs some way to protect its network stack because it is brittle and has more holes than a swiss cheese and two windows machines in the same network infect each other in a second like lepers; but a properly configured GNU/Linux system is protected by the hardware firewall unless you put it in the DMZ. Ahh! And wasting CPU cycles with a bloated, and useless, graphical interface to iptables.

If you are running a public service, the problem is not firewalling the other 64535 closed and unused ports, but making sure that the software controlling the sevice in port 65536 is not vulnerable to external (and internal) attack. You can use the firewall facilities in that service port to make it more robust to attack and penetration, but that is very different to simply "opening and closing" ports. More so, what would you accomplish by "stealthing" a system? Just give a cracker a confirmation that there is a machine there and that it is probably worth attacking it because it must have something valuable, why else would they try to hide it?

---

### Post by Delkster on 2006-07-23
> **dradul said:**
> Believe it or not, the basic difference is architectural. POSIX systems are designed to restrict process execution and file access privileges. You may argue that the basic security model is "primitive" and that is correct in the sense that it is simple and old.
...
Your presumption that malware can act and behave as it does in Win32 systems is based on the widespread belief that applications in POSIX systems have the same kind of unnecesary system-level integration that those OSs have.

The strong separation of privileges with few exceptions certainly makes it more difficult for some types of malware to cause considerable damage, but does that prevent it from spreading or touching the user's personal data? It may have been a mistake to specifically refer to virii in my previous post, as -- according to my understanding, which may not be up-to-date, as I already mentioned -- much weight is nowadays on trojans and worms. Trojans can get their code executed as long as users run them, and there's no reason why privilege separation or other architectural differences would prevent that, although they can limit the damage by, for example, making system clean-up easier by limiting the infection to the user's home directory.

That also means that the trojan, or other possible malware, can access the user's data, as the user and his processes obviously have the privilege to do that. As for means of spreading further from that ground, refer to my previous post.

The kinds of malware that may be effective on Linux are indeed more limited than what Windows and its traditional user culture allow, but that doesn't mean that they wouldn't exist -- and some of them are of the kind that also plagues Windows.

> I am not, under no curcumstance, making the affirmation that POSIX systems are invulnerable. You somehow managed to misquote me and implicitly suggest that I said exactly the contrary of what I just repeated in the previous sentence. No, what I said is that vulnerabilities and the methods of attack are very different.

It's true that in your original post you wrote that the attack vectors aren't unexistent but merely that they're different. That's true, at least as far as traditional viruses and network worms go, as they have a more difficult time affecting systems where strong separation of privileges is enforced and where global access to network services by default is rare. However, while it may have been unintentional, your writing also gave me the impression that protection from malware or, indeed, even caring about the matter, is inherently useless in Unix/Linux, and I felt the need to express my opinion on that. I didn't mean that what you wrote was incorrect in itself.

Again, as I stated in my previous post, right now I wouldn't bother with particular protection software on my Linux desktop either, and care, understanding and knowledge are always the strongest protection against infection. The weakest link tends to be the human factor after all, particularly since it remains vulnerable even after other possible attack vectors have been diminished or even eliminated.

---

