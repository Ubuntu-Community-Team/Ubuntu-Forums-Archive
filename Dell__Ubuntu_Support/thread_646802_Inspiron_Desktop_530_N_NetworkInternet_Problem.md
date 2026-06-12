---
title: "Inspiron Desktop 530 N Network/Internet Problem"
date: 2007-12-21
forum: Dell  Ubuntu Support
---

### Post by SilverDragon on 2007-12-21
I recently ordered an Inspiron 530 N and everything seems to be going fine, except I can't get on the internet. It came with 7.04 and it didn't work and then I installed 7.10 on it and it still doesn't work.

I saw other posts about it where people ran certain commands in the terminal and people gave advice on what they saw. I'd be willingly to try any of those.

My old computer which I had Ubuntu 7.10 installed worked great.This includes the internet and I am still connected to the same cable modem.

Any feedback would be appreciated. :-)

---

### Post by eolson on 2007-12-21
Have you tried turning off WEP or WAP (whichever your modem uses)?  If you can get it working without, then you can turn it back on (might take a few teaks).  Mine took right off with Feisty,  immediatly did an upgrade to Gutsy and it still worked fine.  I'm on DSL with a 2-Wire (something or other) router.

---

### Post by gbrainin on 2007-12-21
I'm not entirely clear from your post: Were you able to access the internet using 7.04, but not 7.10?  Or do you have no internet access with either one?

---

### Post by SilverDragon on 2007-12-22
To gbrainin: I was not able to access the internet with either version.

To eolson: I'm not really sure how to turn WEP or WAP off, but I thought those were for routers.

I was able to fix my problem but I think this might just be a temporary fix. Here are  the steps I went through.

1. I went on my sister's laptop upstairs which is running Windows XP and copied down her DNS servers. 

2. I went into Network Settings and changed the Wired Connection to DHCP, which automatically configures itself. By doing so I also shut off Roaming Mode.

3. I went to the DNS Setting and added the servers I copied down earlier.

4. I disconnected my modem and reconnected it and everything seems to work fine.

At first it seemed slow, but now its working at top speed. Also, I thought using the DNS servers I got from my sister's laptop may effect her internet, but it didn't.

---

### Post by gbrainin on 2007-12-22
Glad you were able to get things working!  It sounds like the original problem was that the settings on your computer were not compatible with your modem and/or internet service.  So doing what you did is probably the correct permanent fix.  You should not need roaming mode, since this is a desktop computer.

In theory, if you are using DHCP you should not have to manually input the DNS server numbers.  However, doing so should not harm anything.  DNS servers are computers on the internet, like web servers, so you using the same ones as your sister should not affect her any more than both of you using Google.

---

### Post by volodya84 on 2008-01-08
How Do I find a DNS address in XP, so I could then enter it into ubuntu? (I have 7.10)

---

### Post by gbrainin on 2008-01-08
I found this on the microsoft website [http://support.microsoft.com/kb/305553]("http://support.microsoft.com/kb/305553"), which explains how to set the DNS address in XP.  You should be able to follow the steps to look at the current setting.

---

