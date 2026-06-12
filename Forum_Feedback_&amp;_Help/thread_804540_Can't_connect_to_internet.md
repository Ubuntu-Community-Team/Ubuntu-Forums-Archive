---
title: "Can't connect to internet?"
date: 2008-05-23
forum: Forum Feedback &amp; Help
---

### Post by ugm6hr on 2008-05-23
There are plenty of people who have this as their first question regarding Ubuntu?  Why?  It is a primary role for computers in the modern day.

Unfortunately, merely telling people that it doesn't work won't help them to resolve the issue.  So - in the words of Tom Cruise, "Help me, help you."

This guide is useful reading regarding getting generic help: [https://help.ubuntu.com/community/GettingAnswers](https://help.ubuntu.com/community/GettingAnswers)

For internet-related help, make sure you include the following details:

1. How were you trying to get online?  e.g. dial-up, USB-wired ADSL modem, ethernet-wired ADSL modem, ethernet-wired ADSL modem-router, wireless router / modem-router, 3G-mobile internet etc.

2. What hardware are you using?  The brand & model number (perhaps with a link to an online manual) for your adapters, modems, routers etc.  You can generally identify external components from their labelling, and internal components from within an Operating System already installed (e.g. Windows or Ubuntu).
```
lspci
lsusb
lshw -class network
```

3. Who is your Internet Service Provider (and in which country)?

4. Which version of Ubuntu are you using?  e.g. Ubuntu 8.04, Xubuntu 7.10 etc and 32- vs 64-bit.
```
uname -a
lsb_release -a
```

5. Can you get online with any other method?  e.g. if you have a wifi problem, can you connect with ethernet?

6. How are you getting online to post on this forum?

7. Include the **output** from the following commands from Terminal (all **case sensitive**).  They help identify your hardware, so provide further detail to potential helpers.  If necessary, just copy and paste the text into a text file and upload from a different computer.

```
ifconfig
iwconfig
route -n
ping -c 3 208.67.219.101
ping -c 3 www.opendns.com
```

8. For wifi - what encryption are you using? Have you tried an open network?  What wifi channel do you use?

9. Do you dual-boot with Windows?  If yes - read this:
From: [http://support.microsoft.com/kb/910389](http://support.microsoft.com/kb/910389)
> If the network adapter supports a power management option, the following check box may be selected:
Allow the computer to turn off this device to save power
If the network adapter supports this option, it is available on the Power Management tab of the network adapter properties dialog box. To resolve this issue, disable this option on the Power Management tab. For more information about how to disable this power management option, click the following article number to view the article in the Microsoft Knowledge Base:

If you have this power-save function on in Windows, it will turn the network card off before shutting down, leaving it unavailable to Ubuntu.  So check that in Windows, and make sure you don't have power-save on.

If you include all these facts, together with an explanation of what you have tried already, your chances of a quick solution are much higher...

---

### Post by forestpixie on 2008-05-23
Did you mean to put this here?

Edit - I mean you should add it to your sticky in Abs Beginners :)

---

### Post by ugm6hr on 2008-05-23
> **forestpixie said:**
> Did you mean to put this here?

It doesn't really belong anywhere - I have linked to it from the ABT beginners sticky.

But figured it was as good here as anywhere else, since it is about forum help.

Just decided to do this to save having to reiterate the same questions over and over.

---

### Post by forestpixie on 2008-05-23
> Just decided to do this to save having to reiterate the same questions over and over.

That would be a BIG sticky - I swear that people think that search engines only work in windows :D

---

### Post by ugm6hr on 2008-05-23
> **forestpixie said:**
> That would be a BIG sticky - I swear that people think that search engines only work in windows :D

Or that we are all psychic mind-readers!

:popcorn:

---

### Post by forestpixie on 2008-05-23
I knew you were going to say that ;)

---

### Post by mips on 2008-10-01
> **ugm6hr said:**
> 
Unfortunately, merely telling people that it doesn't work won't help them to resolve the issue.  So - in the words of Tom Cruise, "Help me, help you."


When I used to be pretty active in the networking section I used to start almost every post with the exact same questions you listed here + a few extras.

A good one for those that dualboot or have an extra Windows PC is to ask for the output of ipconfig /all from a terminal.

I eventually just gave up though as 80% of the questions are the same and few bother to search.

---

### Post by Malac on 2008-10-01
(of topic a bit)

> **mips said:**
> ....few bother to search.
Actually I think the search is sometimes a bit lacking as it seems to search on individual words first instead of phrases first.
So the one which is pertinent to your query is two or three pages in, most new users don't have the patience to go through each thread of those 2+ pages so post a new one.

Just my tuppence.

---

