---
title: "Parental Controls"
date: 2005-06-24
forum: Desktop Environments
---

### Post by livingword26 on 2005-06-24
I have recently installed Ubuntu on an old Gateway computer. I am giving the computer to my 8 year old son, but I want to be able to restrict what web sights he goes to. Ideally I would like to be able to choose a few for him to visit and not allow any others. Any suggestions?

---

### Post by intangible on 2005-06-24
You'll want to look into a program called "DansGuardian" along with "Squid"

Unfortunately there's no GUI to this that I see with Ubuntu, but it's all there.  If you are pretty knowledgable about networking, this shouldn't be hard to set up.  [http://www.dansguardian.org](http://www.dansguardian.org)

---

### Post by coolaj86 on 2005-07-12
Have you had any luck with this? I'm thinking about doing the same thing, but the configuration of squid and dans guardian aren't exactly pleasant from a first glance.

---

### Post by hippyjim on 2005-07-26
[QUOTE=coolaj86]Have you had any luck with this? I'm thinking about doing the same thing, but the configuration of squid and dans guardian aren't exactly pleasant from a first glance.[/QUOTE]

I'll say they're not!!

This thread might be a bit preachy, but all the info you need is in it - [http://www.ubuntuforums.org/showthread.php?p=273410#post273410](http://www.ubuntuforums.org/showthread.php?p=273410#post273410)

This article pretty much takes you through step by step.

[http://software.newsforge.com/article.pl?sid=04/06/23/1521209](http://software.newsforge.com/article.pl?sid=04/06/23/1521209)

Don't forget to flush any iptables rules you've done first, or you'll just go round in circles (as I did for days). 'iptables -t nat -F'

---

### Post by IBLPNZIT on 2005-10-11
Hello all, 

I am new to Ubuntu. I am in need of some assistance, if y'all would not mind.

I administrate a Windows LAN with a Ubuntu box sitting between the LAN and the router. The box has 2 network cards in it. The 1st receives traffic from the LAN (acting as a proxy), the 2nd sends the traffic (once appoved by dansguardian) to the router to get to the Net. I had someone else install Ubuntu for me, since I was not very knowledgeable. The default level I have dansguardian set at is "too harsh" - I need to change its level or attributes. Does anyone know...

1. Where to find config files for dansguardian?
2. How to change them?

Any help would be great,

Joshua Goodwin
IBLPNZ IT Department

---

