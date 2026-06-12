---
title: "Upgraded from 7.04 to 7.10. Help :("
date: 2008-11-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by arvadawest on 2008-11-06
Hi All,

We had previously opened a thread with no response (or of no help), so we thought we would try again for your help.

We upgraded our Ubuntu OS from 7.04 to 7.10 (Gutsy Gibbon).  When this update was completed were are unable to browse the Web and cannot get any updates.  We have checked all our network settings (IP, Subnet, Gateway, DNS, etc) and all is ok.  We were able to ping IP addresses and fully qualified domain names with good response times, but when it comes to port 80 we cannot browse and cannot connect to get updates.  This happened a week ago and so we are having to borrow a pc to post this.

Can someone please help us (and please be nice we had some responses there were not professional).  We appreciate your help so much.  Keep in mind we are Linux newbies.  Thank you.

-aw

---

### Post by kerpow on 2008-11-06
What a strange problem to be having, please accept my sympathies, how can one trouble-shoot without (ready) access Google! :)

If you boot from an alternative live CD can you get to web pages then?

Have you ever needed to, or tried to setup access via a proxy server?

---

### Post by munchy4444 on 2008-11-06
Sometimes trying a fresh install fixes some stuff, thats what I had to do for Intrepid.

---

### Post by arvadawest on 2008-11-07
Thank you for the replies.  We are borrowing a pc tonight to read any postings to our posting.

Does anyone have a fix to our problem?  We really need a fix to this as we cannot use our Ubuntu system.  We really need help from you experts.  Thank you so much.

-aw

---

### Post by arvadawest on 2008-11-09
Hello,
We are updating this to put it at the top of the list in hopes that someone can help us.

Is there anyone we can contact over the phone or email with help with this problem.  We thank you all so very much.

-aw

---

### Post by Linicks on 2008-11-09
Interesting.

Could be anything, but try a few things.

Have you used different browsers?  i.e. try (hit q to exit):

links [www.google.com](www.google.com)

Is the firewall running?  Try flushing it (no need to add to init.d here, just run it once):

[http://www.cyberciti.biz/tips/linux-iptables-how-to-flush-all-rules.html](http://www.cyberciti.biz/tips/linux-iptables-how-to-flush-all-rules.html)

Does wget work?  What about e-mail - can you send/receive mails?  FTP?

What does ifconfig look like?

EDIT:  Have a read of this too, so good tests to do here and things to check:
[http://www.cyberciti.biz/tips/linux-network-diagnose-tools.html](http://www.cyberciti.biz/tips/linux-network-diagnose-tools.html)
Also, as kerpow stated, boot from a LiveCD.  That will at least test the network card is OK, and also you will not have to borrow a computer to access the Internet to investigate this issue.

Nick

---

### Post by arvadawest on 2008-11-09
> **Linicks said:**
> Interesting.

Could be anything, but try a few things.

Have you used different browsers?  i.e. try (hit q to exit):

links [www.google.com](www.google.com)

Is the firewall running?  Try flushing it (no need to add to init.d here, just run it once):

[http://www.cyberciti.biz/tips/linux-iptables-how-to-flush-all-rules.html](http://www.cyberciti.biz/tips/linux-iptables-how-to-flush-all-rules.html)

Does wget work?  What about e-mail - can you send/receive mails?  FTP?

What does ifconfig look like?

EDIT:  Have a read of this too, so good tests to do here and things to check:
[http://www.cyberciti.biz/tips/linux-network-diagnose-tools.html](http://www.cyberciti.biz/tips/linux-network-diagnose-tools.html)
Also, as kerpow stated, boot from a LiveCD.  That will at least test the network card is OK, and also you will not have to borrow a computer to access the Internet to investigate this issue.

Nick

Thank you Nick.  We will read the article you typed.  But, we have checked all the network settings and we can Ping IP addresses and fully qualified domain names. The network card is fine because for the fact that we can ping.  It's just port 80.  I have never known this kind of issue.  Thank you Nick.  We will check into what you typed.  If you have anything else, please let us know.  I have never used Live CD so not sure what that is.  We will look into that.  Thank you.  -aw

---

### Post by kerpow on 2008-11-10
> **arvadawest said:**
> I have never used Live CD so not sure what that is.

The Live CD that we speak of is the CD that you use to install Ubuntu.  If you boot from it you can use Ubuntu from the CD 'Live' before or instead of installing it.

Grab the CD you installed 8.04 from, boot from it and redo some tests.  From this you should get an idea if this issue is anything to do with your hardware's reaction to 8.10 or something else.

Also, have you ever tried to, or needed to configure your PC to use a proxy server?  Does your ISP require you to use a proxy server?  If you are not sure, could you tell us, how do you connect to the net?  Dial up, DSL, cable?  Is the modem internal or external?  If external is it connected with a USB cable or a different type of cable?

Hang in there, I am sure we can get you up and running again.

---

### Post by arvadawest on 2008-11-10
> **kerpow said:**
> The Live CD that we speak of is the CD that you use to install Ubuntu.  If you boot from it you can use Ubuntu from the CD 'Live' before or instead of installing it.

Grab the CD you installed 8.04 from, boot from it and redo some tests.  From this you should get an idea if this issue is anything to do with your hardware's reaction to 8.10 or something else.

Also, have you ever tried to, or needed to configure your PC to use a proxy server?  Does your ISP require you to use a proxy server?  If you are not sure, could you tell us, how do you connect to the net?  Dial up, DSL, cable?  Is the modem internal or external?  If external is it connected with a USB cable or a different type of cable?

Hang in there, I am sure we can get you up and running again.

Hi and thank you Kerpow.  We will try using the LiveCD. Actually, we had version 7.04 and upgraded to 7.10 and that's when the problems began.  We never had 8.04.

We use cable for our ISP so we do not use a proxy server.  We had to admit that we've never seen something like this when all the network settings are ok and Pinging is fine as well.  Just the port 80 seems to be the issue and unable to get any updates for 7.10

Have you ever read anything like this before?

We will try the LiveCD.  We assume it is on the Ubuntu 7.04?  We sure wouldn't want to do a complete reinstall, so we hope that this would be a last resort.  

Thanks Kerpow.  We really appreciate any help you or anyone here can help us.  We are disappointed because we wanted to get away from windows.  Funny how we are having to borrow a pc now.  Thank you for your kindness.  -aw

---

### Post by kerpow on 2008-11-10
7.04, right, sorry I did read that but typed 8. :)

Try 7.04 or any Live CD to test your internet connection.  Don't install just test from the CD and see what happens.  If it works, then we can focus 100% on your Ubuntu installation being at fault, if not we might want to look elsewhere.

Another thing to look at:

On your cable setup, do you have a cable modem?  And if so do you connect to the cable modem via an ethernet cable?  If so there are oftern mini HTTP servers built into them.  If we can find the IP of the modem you can try 'browsing' to the modem (via port 80) on your installed Ubuntu.  If this works (ie shows a config page - or login page - or anything other than page not found) it will prove that your Ubuntu works and we need to focus on the modem and ISP.

Have I seen this before?  Well, yes, but all the times I can remember it has been some sort of firewall.

I know it looks like Ubuntu is at fault as it seemed to stop working after the upgrade, and I don't doubt that it could be.  By trying these classic fault finding techniques we are cornering the problem, each step getting closer to the fault.  By jumping straight into what we think the fault might be we run the risk of waiting lots of time and getting confused as to what tested as good and what did not.

Having said all that, I bet you the next poster will come right in with the correct fix stright off! :)

---

### Post by arvadawest on 2008-11-10
> **kerpow said:**
> 7.04, right, sorry I did read that but typed 8. :)

Try 7.04 or any Live CD to test your internet connection.  Don't install just test from the CD and see what happens.  If it works, then we can focus 100% on your Ubuntu installation being at fault, if not we might want to look elsewhere.

Another thing to look at:

On your cable setup, do you have a cable modem?  And if so do you connect to the cable modem via an ethernet cable?  If so there are oftern mini HTTP servers built into them.  If we can find the IP of the modem you can try 'browsing' to the modem (via port 80) on your installed Ubuntu.  If this works (ie shows a config page - or login page - or anything other than page not found) it will prove that your Ubuntu works and we need to focus on the modem and ISP.

Have I seen this before?  Well, yes, but all the times I can remember it has been some sort of firewall.

I know it looks like Ubuntu is at fault as it seemed to stop working after the upgrade, and I don't doubt that it could be.  By trying these classic fault finding techniques we are cornering the problem, each step getting closer to the fault.  By jumping straight into what we think the fault might be we run the risk of waiting lots of time and getting confused as to what tested as good and what did not.

Having said all that, I bet you the next poster will come right in with the correct fix stright off! :)

Thanks Kerpow.  I ran many tests on this machine.  I connected it directly to the cable modem (it normally is behind an enterprise firewall) and still it didn't work.  I could still Ping and traceroute, but nothing on port 80; so the NIC is working fine.  I went through everything I could using the OSI model except for layer 7.  I began to think it was the browser, but that didn't work.  To make a very long story short, and now I feel stupid--I am running Firestarter on this machine and for sometime reason it change the outbound policies and this is why I was unable to browse.  Once I made the change, it works!

One thing, I tried to boot using the Ubuntu CD (v 7.0.4) using LiveCD, but I was unable to find this feature.

I want to thank you for your help.  My stupidity and overlooking Firestarter.  I am newbie to Lunix, so it is difficult for me (us).  With two new pc's coming in, now we need to find out how we can use this as our future file server so Windows machines can see this Lunix box.

Again, our sincerest appreciation for you taking the time to help us.

-AW

---

### Post by kerpow on 2008-11-12
Hey, its all good.  You are not going to be the first or last, and this forum thread will help others (I hope).  

Glad to have you back on the net!

---

