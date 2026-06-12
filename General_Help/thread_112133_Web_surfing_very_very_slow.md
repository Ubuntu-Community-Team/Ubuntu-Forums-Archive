---
title: "Web surfing very very slow"
date: 2006-01-03
forum: General Help
---

### Post by noneofthem on 2006-01-03
Hey, there!

Before I start I have to say that I am quiet new in Linux. However I have more than 16 years of experience with computers in general so if someone answers he may answer in a normal way. Meaning: Please don´t assume I am someone who only knows common Windows XP tasks. Thanks.

I just installed Ununtu 5.1 on my laptop (details below) and I am more than happy about how great everything runs. I also got most of my needed applications installed and everything is great. Except one thing.

When I use Firefox (1.07, 1.5) or any other browser the websurfing appears to be more than slow. Under Windows XP everything appears within seconds (I have a 2MBit broadband connection, wireless). Under Ubuntu it takes about 15 to 30 seconds until the browser starts to even look for something. Once I am on a website the browsing gets a bit faster withing the site. But if I change the location again I have to wait again.

I don´t know what to do and I hope someone has a solution or experienced something similar so we can solve this problem. As I said everything else (wireless LAN, updates, installing software, office etc.) runs perfectly. I just suffer this very slow surfing experience.

I am looking forwardto hear from anyone. Thanks in advance and a happy new year!

Amir

---

### Post by Swab on 2006-01-03
First thing you might want to try:

Type about:config into the firefox address bar.

Use the filter to search IPv6, and set network.dns.disableIPv6 to true

---

### Post by handy on 2006-01-03
Have a look here:

[http://ubuntuforums.org/showthread.php?t=88639&page=2](http://ubuntuforums.org/showthread.php?t=88639&page=2)

Go down the page looking for **_Internet Stuff:_**

This covers the **IPv6** stuff & **DHCP**, it could solve your problems, it solved mine.  :p 

handy

---

### Post by noneofthem on 2006-01-04
Hey,  guys!

Thanks a million for your replies! I will try that later. Gotta go now. I will let you know if it worked out for me. Thanks!

Amir

---

### Post by noneofthem on 2006-01-04
Hey again!

I couldn´t wait and gave it a try! And everything is brilliant now! Even faster than under windows!

Thank you guys a lot!

Have a good one!

Amir

---

### Post by bionnaki on 2006-01-04
the default firefox with ubuntu is quite slow. update to 1.5

[https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29](https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29)

---

### Post by handy on 2006-01-08
My **old** Firefox v1.0.7, is pretty quick, I look forward to 1.5, but I think I'll wait until Dapper does it for me, due to a bad upgrade experience, that took Firefox away altogether. :confused: 

handy

---

### Post by dcstar on 2006-01-08
[QUOTE=handy]My **old** Firefox v1.0.7, is pretty quick, I look forward to 1.5, but I think I'll wait until Dapper does it for me, due to a bad upgrade experience, that took Firefox away altogether. :confused:

handy[/QUOTE]
After "stalling" for the basically same reasons you have, I finally installed 1.5 a couple of days ago (my 1.07 is still functional), it was well worth the effort.

Just read this thread to learn from the experiences of others:

[http://ubuntuforums.org/showthread.php?t=79283](http://ubuntuforums.org/showthread.php?t=79283)

---

### Post by slux on 2006-01-08
The GNU/Linux way may currently be bad for people who want the latest and greatest and want it fast but I feel Ubuntu tremendously alleviates the problem with their regular 6 month update intervals. It's still a problem for some apps and some of us will always be early adopters but for me personally it's enough that I'll get it in Dapper. Doesn't seem revolutionary anyway. Were this Debian, you might have to wait 2 years in the worst case scenario and that's something I find unacceptable.

---

### Post by handy on 2006-01-09
I must be getting old, I am in no hurry anymore, I'm happy with what I've got.:KS 

I don't need to spend hours on tweeking & carrying on now, when someone else will give it to me allready done later! :KS 

Nobody will put Wine on for me, so I used Arnieboy's Automatix, for Wine & a lot of the other app's, drivers, codecs, updates & what have you that I could choose from.

Then I installed WineTools to improve the Wine setup & make it a lot easier.

If you like to do it the hard way great, there are lots of hard thing to do on Ubuntu (Linux), if your new to it why create stress, do what you have to, & wait for the next distro' I say...

handy

---

