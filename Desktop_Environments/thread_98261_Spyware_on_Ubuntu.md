---
title: "Spyware on Ubuntu?"
date: 2005-12-02
forum: Desktop Environments
---

### Post by zeeone on 2005-12-02
I'm relatively new to linux and totally new to Ubuntu. So far I really like it and it does look to me like it the *one* distro for me.
I've been reading the forums here and one thing that everyone is mentioning when it comes to comparing Windows and Linux is spyware.
Can anyone, please explain to me why and how come there can be no spyware in Linux?

Much appreciated!

---

### Post by dcstar on 2005-12-02
[QUOTE=zeeone]I'm relatively new to linux and totally new to Ubuntu. So far I really like it and it does look to me like it the *one* distro for me.
I've been reading the forums here and one thing that everyone is mentioning when it comes to comparing Windows and Linux is spyware.
Can anyone, please explain to me why and how come there can be no spyware in Linux?

Much appreciated![/QUOTE]

To be exceptionaly brief, in Linux all of the source code is available to be examined for any vulnerabilities, so they can be fixed ASAP.

Windows (and other) code is proprietary  and usually kept confidential, so any issues with security holes (or "features") that allow things like Spyware to function are harder to identify (until someone finds them, and then a way to exploit them) and you have to wait for the controller of the software to fix them.

---

### Post by grsing on 2005-12-02
There could be spyware on Linux (some spyware is caused by stupid/ignorant people clicking on whatever pops up and agreeing to anything), but the market among Linux users probably is much more wary about that sort of thing, and it's a very small market compared to Windows anyway, so no one bothers.  And the more insidious type like dcstar was talking about doesn't work for those technical reasons.

---

### Post by zeeone on 2005-12-02
Thanks for your replies!

dcstar, is there a central authority that will go over each line of code to analyze it for potential trojan horses, backdoors and spyware? If not, then keeping spyware away from Linux is an impossible task. The more it gets popular the more it will be a target for spyware.

grsing, from what I gather from your message, yes there can be spyware for Linux but there is none coded yet. That means that there is no anti-spyware software developed yet either. That kind of makes Linux more vulnerable and insecure than Windows.

I'm not trying to give you guys a hard time, I'm just trying to understand the system. I'm migrating from WinXP with MS Antispyware Beta and ZoneAlarm Pro and so far it looks like I'm not more protected in Linux.

---

### Post by cwaldbieser on 2005-12-02
[QUOTE=zeeone]Thanks for your replies!

dcstar, is there a central authority that will go over each line of code to analyze it for potential trojan horses, backdoors and spyware? If not, then keeping spyware away from Linux is an impossible task. The more it gets popular the more it will be a target for spyware.

grsing, from what I gather from your message, yes there can be spyware for Linux but there is none coded yet. That means that there is no anti-spyware software developed yet either. That kind of makes Linux more vulnerable and insecure than Windows.

I'm not trying to give you guys a hard time, I'm just trying to understand the system. I'm migrating from WinXP with MS Antispyware Beta and ZoneAlarm Pro and so far it looks like I'm not more protected in Linux.[/QUOTE]
It is somewhat harder to write spyware for *NIX systems because you typically need root access to install programs system wide or listen on reserved ports.

That said, anyone can make a program that uploads the contents of your user directory to an FTP site if you choose to run it.

Normally, the software you install on a distribution like Ubuntu does come from a central repository, and when you download it, it is verified against an md5sum so you know you don't have a version that has been tampered with.

Moral of the story: if you run random software, it can do things that you don't want it to do.  A sane security approach like you find in many GNU/Linux systems can mitigate some of the damage, but it pays to do a little research.  An ounce of prevention is worth a pound of cure.

---

### Post by PizzAp on 2005-12-02
Wow, this is soo... lol

Sorry. If you install linux software from untrusted sources or use source code, without reading it, from untrusted sources you are indeed in danger. 

Let me assure you, we have all kinds of malware, rootkits, viruses(2 i think), worms, you name it.

There exists a multitude of anti-malware software, rootkit hunters, virus 
scanners, etc.
Apart from that linux offers some architectural benefits, no one is working as administrator for example.

Since linux spyware had to run in userland it would be much harder to code it.
Gator for example hooks the winsock api to intercept all your network traffic if i remember correctly, this would only work as superuser on linux.

Software in ubuntu runs through a certain process, which involves some kind of quality control.
First the coders work on their projects, this is what is called 'upstream'.
They will check every patch they get, they limit write access to their code repositories. If they are ready they release packaged versions of the code.
The ubuntu maintainers take the code, compile and package it for ubuntu.
Some maintainers read some of the code, too. If the maintainers think the software is working, they upload it to the ubuntu servers.

The users then download it from there. The packages are signed to help against tampering, too. If there is a security issue, someone, anyone, can file bug against the package and a new, fixed version will be available soon.

If you think about spyware some more, you will see there are different types, certain cookies could be considered spyware for example.
But i guess you are talking about the unwanted installation of third party software.
If you want to know what you can do against linux spyware know, please be more specific.

You are right, the more popular linux gets on the desktop, the more malware will be written. 
Linux is quite popular and successfull on servers by the way and has strong server security. 
Stronger than windows in any case. (which isn't really hard to accomplish)

Zone Alarm... ms anti spyware beta, get your windows boxes some real defense, please!
Ah, no, don't, just switch to linux.

---

### Post by shaggydoo on 2005-12-02
Linux is a minority in the desktop OS market. There is no "central authority" to validate code, but rather MANY users (different distributions have more/less users) that contribute code to projects. There are some more centralized parts, though, such as the kernel.

Why is Windows more vulnerable?
**Browser**: Well, Internet Explorer has many faults that are easily exploitable. Most of the population uses this browser. Using Firefox? It has many issues as well, but: **1)** being a minority, most people don't attempt as much, because I'm guessing if your site has enough of a Firefox userbase, you're probably not the type to want to exploit them, **2)** it's open-source, so when any issues are found they are reported. The most severe ones are immediately addressed.

**Patches**: While Microsoft makes many of them, lots of bugs are ignored, many are INCREDIBLY delayed.

**Compatibility**: Most virii and exploits are OS-dependant. Meaning, if you're trying to exploit a bug by replacing a file, let's say C:\Program Files\Internet Explorer\iexplore.exe, it won't work due to the filesystem used by Linux.

An important point: THERE ARE VIRUSES/SPYWARE FOR LINUX! If you want to be protected, there are anti-virus and firewall solutions you can use. Just check Synaptic for some simple choices, or google for what else you can find.

---

### Post by dto on 2005-12-02
Funny that I just stumbled onto [this little article](http://www.eweek.com/article2/0,1759,1884318,00.asp?kc=EWYH104039TX1B0000665) right after I read the original post. :)

---

### Post by zeeone on 2005-12-02
Thank you everyone for your replies!

---

### Post by Danielle on 2005-12-03
hi, i think for any spyware to run it would have to be a rootkit so all you would need is a good rootkit scanner for protection.

is that correct?

---

### Post by bionnaki on 2005-12-03
sudo apt-get install chkrootkit

run by typing chkrootkit in a terminal

---

### Post by paradj on 2006-08-30
[Rootkit Hunter]("http://www.rootkit.nl/")
[http://www.rootkit.nl/](http://www.rootkit.nl/)

ms
:shock: :confused:
:mad: :twisted: :evil:
](*,)
:idea:
UBU!
8)

---

