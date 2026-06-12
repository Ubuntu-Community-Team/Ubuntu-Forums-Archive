---
title: "user space barrier, password change and &quot;surf protection&quot;"
date: 2005-04-10
forum: Desktop Environments
---

### Post by pirast on 2005-04-10
Hi,
we want to have a PC in our classroom and we think there must be Ubuntu installed (no license costs, easy, looks nice, completely free, debian based and nice phiolosophy).

But I have three questions:
1. Every student should have an own user account. That's no problem, but every student should have a barrier how much he/she is able to save on the harddisk. How can I realize this?

2. When a student is logging in first, he should be forced to change his/her password. How can I realize this?

3. The PC will be connected to the internet. Is there any opensource solution to filter sex sites etc.? When it is proxy based: How can I force the users to use the proxy?


Any ideas?  :) 

Greetings,
Martin
//Edit sorry I didn't read "*read* This Is Not The Place To Ask Questions!"  ](*,) 
Could anybody move this thread?

---

### Post by matid on 2005-04-10
[QUOTE=pirast]1. Every student should have an own user account. That's no problem, but every student should have a barrier how much he/she is able to save on the harddisk. How can I realize this?[/quote]
```
sudo apt-get install quota quotatool
```
Then read quotatool manual.
[QUOTE=pirast]2. When a student is logging in first, he should be forced to change his/her password. How can I realize this?[/QUOTE]
```
passwd -e **username**
```
[QUOTE=pirast]3. The PC will be connected to the internet. Is there any opensource solution to filter sex sites etc.? When it is proxy based: How can I force the users to use the proxy?[/quote]
You can try some Firefox extension if you want it computer based.
If computers are connecting to the Internet through server or router you can try making proxy transparent (force every connection on port 80 to go through proxy) and then install some filter.

---

### Post by localzuk on 2005-04-10
[QUOTE=pirast]Hi,
we want to have a PC in our classroom and we think there must be Ubuntu installed (no license costs, easy, looks nice, completely free, debian based and nice phiolosophy).

But I have three questions:
1. Every student should have an own user account. That's no problem, but every student should have a barrier how much he/she is able to save on the harddisk. How can I realize this?

2. When a student is logging in first, he should be forced to change his/her password. How can I realize this?

3. The PC will be connected to the internet. Is there any opensource solution to filter sex sites etc.? When it is proxy based: How can I force the users to use the proxy?


Any ideas?  :) 

Greetings,
Martin
//Edit sorry I didn't read "*read* This Is Not The Place To Ask Questions!"  ](*,) 
Could anybody move this thread?[/QUOTE]
 1. Have a look at the 'quota' package for disk quotas. - I will post more info when I have some...
2. Run 'sudo chage -d 0 username' for each user, as this forces immediate password alteration.
3. I am not sure about this - never had to set one up yet...

---

### Post by pirast on 2005-04-10
Hi,
thanks for your answers.

1. I think, I'll get it working with quota, but I am thankful for tips how to get quota working.

2. The second thing worked without problems here.

3. That's the remaing problem. I thougt too that it can be realized by using a proxy. But the users can deactivate the proxy (in the browser preferences) or am I not right?

And I didn't find any easy to install web filtering open source solution  :? 

When there isn't any free solution I think we must do it without a web filtering solution  :|

Greetings  :-) ,
Martin

---

### Post by Diff on 2005-05-23
"3. That's the remaing problem. I thougt too that it can be realized by using a proxy. But the users can deactivate the proxy (in the browser preferences) or am I not right?

And I didn't find any easy to install web filtering open source solution"

I also was looking for a "easy" way to install web filtering and I think I found one. I've just collected all the howto's and plan to install it all in next couple of weeks on a private home network. This is what I have:

1. Use a proxy like squid and use squidguard as a free combined filter, redirector and access controller plugin ([http://www.squidguard.org/intro/](http://www.squidguard.org/intro/))
Squid is fully supported bij Ubuntu (use synaptic or apt to get it)

2. On [http://www.bn-paf.de/filter/#setup](http://www.bn-paf.de/filter/#setup) explanation off how to install and get squidguard and get blacklists

3. More about firewall Squid as a transparent proxy take a look at [http://www.securityfocus.com/infocus/1431](http://www.securityfocus.com/infocus/1431)

I use shorewall as the firewall between the homenetwork and the internet. For a transparent proxy in shorewall to force the users to use the proxy server for web and ftp use the next 3 rules must be enough:
REJECT	loc:!<proxy ip>	net	tcp	80
REJECT	loc:!<proxy ip>	net	tcp	443
REJECT	loc:!<proxy ip>	net	tcp	21
Put these rules in de /etc/shorewall/rules

I don't know of this works yet but it looks like a nice solution to me :-) .

Frans

---

### Post by pirast on 2005-05-23
Thanks, but it will take some time till there will be a pc with Ubuntu in our class.

Please tell us whether it works or not  :) 

Thanks,
Martin

---

### Post by poofyhairguy on 2005-05-23
moved. Thanks for admitting to your error, most don't.

---

### Post by Burgundavia on 2005-05-24
You are a prime candiate for Edubuntu:

[http://udu.wiki.ubuntu.com/Edubuntu](http://udu.wiki.ubuntu.com/Edubuntu)

Can you contact those people and chat with them regarding you specific needs?

Corey

---

