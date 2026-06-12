---
title: "Dell Mini 1012 Wireless not working on Battery Power"
date: 2010-03-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Kevin Dunlap on 2010-03-31
[COLOR=black][FONT=Verdana]I recently purchased a Dell Mini 1012. After Installing Ubuntu 9.10, the wireless connection stops whenever i switch to battery power. Why am I experiencing this behavior? What can I do to resolve it?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thanks in advance for the help.[/FONT][/COLOR]

---

### Post by youngrob on 2010-06-01
I have this problem as well.  I just loaded 10.04 and whenever I run the machine on battery power the wireless does not work.  

This is the only post I have seen on the subject.  Did you have any luck fixing the problem?

---

### Post by thehumble1 on 2010-06-19
I don't have the problem. I'm wondering if you have different hardware than I have, maybe a BT card or GSM card. I have no 3g/GSM card nor BT and am running 10.04 netbook remix. 

Also, how did you install your wireless drivers when you started? I used the bcmwl packages which work fine and don't fail on battery power.

---

### Post by twoshadetod on 2010-06-23
Exact same problem,but happens on windows and ubuntu.  Seems like without the battery sometimes it will work in the beginning then fail.  I have about 2 days left to return this to walmart and am about to bring it back if I can't find a solution.

---

### Post by Boquito17 on 2010-06-26
Hey everyone

Recently installed Ubuntu on my Dell Mini 1012 as well. At first, I was having difficulty getting my WiFi working, but used ethernet to install some updates and all went well, including my WiFi. Yesterday, if I remember correctly, it stopped working when I went onto battery power, and even when I connected power to it.

OK, seems like I found a fix. 

I went to Sytem > Administration > Hardware Drivers

Here, it brought up two options. I have changed them before, but can't remember which one was the correct one. Anywho, I activated the Broadcom STA wireless driver and it seemed to work on power. I disconnected and it worked! I'm hoping I won't bump into any other problems. 

Yesterday, while searching on my windows side, I came across an application for WiFi Management, which I will post up here if I find it :P

Hope I helped! Seemed to help me. :D

---

### Post by bodek on 2011-02-21
Hello to all,
Noticed this post is old, but don't know if this issue was solved.
The other day I got hold of Dell Mini 10 (1012) and tried to install Ubuntu 10.4. All was well, but the network didn't work when on battery power, neither wired nor wireless. In fact I've noticed the same problem in Win 7 Starter that came with the notebook.
Tried to google for a solution, but didn't find anything. This post seem to touch the issue, but still don't have any clue.
Please, can anybody shed some light on this issue?

---

### Post by amchornet on 2011-02-21
Hello all, I just purchased a dell 1012 and installed ubuntu 10 on it. The first time I did it my network worked but only for 15 mints. So then I repartitioned the drive and reinstalled ubuntu.  This time I did the install with the earth-net cable hooked up. I had ubuntu install all of the updates and third party stuff all at once and then after I unplugged the earth-net cable everything was fine. I just had to do the install with a land-line for updates with the install.  Hope this helps

---

### Post by bodek on 2011-02-22
Don't know if I'm getting somewhere but it seems that there might be a 'mechanical' problem. Apparently when the power adaptor is plugged in (even if not connected to power) the network works.
Just have to run some more 'tests'.

---

