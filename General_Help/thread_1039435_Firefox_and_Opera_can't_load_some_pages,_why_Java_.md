---
title: "Firefox and Opera can't load some pages, why? Java and Flash are working fine..."
date: 2009-01-14
forum: General Help
---

### Post by Benic on 2009-01-14
This bug is making me crazy! I subscribe to online newspaper and I can't go to their site, because most of the time Firefox 3.0.5 (and Opera 9) won't load the page correctly. It happens when Firefox is receiving the data. At this moment, it simply stops. If I restart, it doesn't change anything. Flash works correctly, so does Java (at least as far as I know when I go to the Java test page). I'm using Fasterfox so I turned it off: same problem. I tried to turn off every plugin, even uninstalled then reinstalled them. Nothing works! I changed DNS servers, hoping that it might do it. Nothing, nada, rien!

The most intriguing thing is that the problem doesn't happen all the time. This morning all was going fine and when I came back after lunch, it came back.

I'm totally puzzled :confused:

---

### Post by HunterK on 2009-01-14
What are the sites you are trying to connect to?  Since its happening in both FF and Opera, I guess you can rule out the actual browser as being a problem.

---

### Post by jfcous on 2009-01-14
I am having a similar problem - trying to connect to a bank site and the log in page flashes and then disappears - the rest of the page loads but the log in portion is not visable.  Happens in both Opera and Firefox.  It seems the page is loaded in two steps and the first "loading" ie the log in section is overwritten/superceded by the second "loading" which has general site ads.

would appreciate andy assistance.


jfcous

---

### Post by Benic on 2009-01-14
Two exemples would be [www.economist.com](www.economist.com) and [www.ebay.ca](www.ebay.ca). Even ubuntuforums won't load sometimes.

---

### Post by Benic on 2009-01-14
> **jfcous said:**
> I am having a similar problem - trying to connect to a bank site and the log in page flashes and then disappears - the rest of the page loads but the log in portion is not visable.  Happens in both Opera and Firefox.  It seems the page is loaded in two steps and the first "loading" ie the log in section is overwritten/superceded by the second "loading" which has general site ads.

would appreciate andy assistance.


jfcous

Exactly: the common feature of the sites I can't access is the fact that they have a login to access restricted content.

---

### Post by jfcous on 2009-01-14
It occurs to me that this only happened within the past 30 days or so.  I had no problems prior to recent updates.

jfcous

---

### Post by Benic on 2009-01-14
> **jfcous said:**
> It occurs to me that this only happened within the past 30 days or so.  I had no problems prior to recent updates.

jfcous

Are you using 8.04 or 8.10? 

Like you, I didn't notice anything until recently. I upgraded to 8.10 in october or november and soon after that the problem started.

---

### Post by hyperdude111 on 2009-01-14
ubuntuforums always fails to me with a 503 error. I think their server is very poor. Have you noticed since it was down yesterday the thanking system has disappeared???

---

### Post by Benic on 2009-01-15
> **hyperdude111 said:**
> ubuntuforums always fails to me with a 503 error. I think their server is very poor. Have you noticed since it was down yesterday the thanking system has disappeared???

They did some cleaning and update earlier this week, that probably explains why. About the thanking system, it's over now: no more thanking.

---

### Post by Benic on 2009-01-15
I tried both Sun Java and Open Java (JDK) this morning, in case one would work, but I still have the same problem. Firefox seemed to run a bit faster with JDK-Icedtea plugin. It's the only difference noticed between the two versions. 

I recently made a fresh install (8.10) on my Dell laptop and I decided not to update Firefox (still version 3.0.3) nor Java. So far, so good. 

I suspect therefore a problem with Java. That would explain why it happens with both Firefox and Opera.

---

### Post by Benic on 2009-01-16
Bump...

---

### Post by digital-daniel on 2009-01-17
I've had exactly the same problem and have been watching this threat.  I've had problems with two sites in particular. [www.fastweb.it](www.fastweb.it) and [www.samsung.com](www.samsung.com) 

I use ubuntu 8.10 and I've been fiddling with synaptic manager (sorry I'm not terribly technical as I'm only on week two of using Linux) something I've done has solved the problem on my machine. 

After the post suggesting it was something to do with Java I began clicking various things with java in the title in the synaptic manager and it's solved the problem, I have no idea which one solved the problem because I wasn't particularly scientific with my approach. 

I now need someone else to help me tell you how I fixed it. Is there something I can call up which will tell me what I've installed and paste it on here?

I'm feeling pleased with myself but a little frustrated I can't tell you how I did it.

Regards,

Daniel

---

### Post by timreed on 2009-01-17
Can anyone tell me how to  remove Opera . I recently installed it and can not find uninstall. getting the best of me. tried deleteing the opera files but they seem to be locked..

---

### Post by Arup on 2009-01-17
> **timreed said:**
> Can anyone tell me how to  remove Opera . I recently installed it and can not find uninstall. getting the best of me. tried deleteing the opera files but they seem to be locked..

If you installed via the deb file all you have to do is sudo apt-get --purge remove opera to completely remove Opera along with its config files.

---

### Post by timreed on 2009-01-17
help.. I recently installed Opera Browser and I can uninstall it. I tried ti delete the opera files but there seems to be a lock on them. Wont let me delete them. What kind of program has no uninstall..help

---

### Post by Benic on 2009-01-17
> **digital-daniel said:**
> I've had exactly the same problem and have been watching this threat.  I've had problems with two sites in particular. [www.fastweb.it](www.fastweb.it) and [www.samsung.com](www.samsung.com) 

I use ubuntu 8.10 and I've been fiddling with synaptic manager (sorry I'm not terribly technical as I'm only on week two of using Linux) something I've done has solved the problem on my machine. 

After the post suggesting it was something to do with Java I began clicking various things with java in the title in the synaptic manager and it's solved the problem, I have no idea which one solved the problem because I wasn't particularly scientific with my approach. 

I now need someone else to help me tell you how I fixed it. Is there something I can call up which will tell me what I've installed and paste it on here?

I'm feeling pleased with myself but a little frustrated I can't tell you how I did it.

Regards,

Daniel

To make a list of installed packages, open a terminal and type:

```
dpkg --get-selections > installed-software
```

Go in your home folder, look for a file named 'installed-software' (you can give it another name by changing installed-software in the terminal). Just attach this file in a reply and we'll be able to look at what you have installed or if you find the packages you're talking about, you can simply paste their names.

---

### Post by digital-daniel on 2009-01-18
Bad news in that I had to do a reinstall  due to another problem and I'm back to square one  retracing my steps. 

So far no luck, random clicking failed. 

Frustratedly yours


Daniel

---

### Post by Benic on 2009-01-19
Well, since nobody has any idea about a way to solve this problem and since I'm getting tired of looking around for a solution, I will reinstall 8.10 (for the third time). If it doesn't work, I will simply trash 8.10 and go back to 8.04. I'm having several issues with Ibex, so I won't mind. I'm wasting way too much time on this distribution trying to fix it...

---

### Post by Benic on 2009-01-21
Update: fresh install and 8.04 install didn't do the work. I shut down Guarddog, same results. At least, it's not a problem with the firewall. 

At home, I don't have problems with my Dell laptop running with 8.10. Could it be related to my internet connection? I use a diffrent internet provider at home.

---

### Post by Benic on 2009-01-21
Finally, I found a solution in this [_thread_]("http://ubuntuforums.org/showthread.php?t=959637&highlight=ipv6"). It's a TCP window scaling problem. You will find some good explanations and workaround there.

Thank you guys!!!!!!!!!

---

