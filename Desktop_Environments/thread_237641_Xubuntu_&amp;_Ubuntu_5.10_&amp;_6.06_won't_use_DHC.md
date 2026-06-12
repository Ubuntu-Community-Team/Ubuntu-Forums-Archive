---
title: "Xubuntu &amp; Ubuntu 5.10 &amp; 6.06 won't use DHCP DNS"
date: 2006-08-16
forum: Desktop Environments
---

### Post by ntgooroo on 2006-08-16
Hardware: Compaq Armada M700

I have tried Ubuntu 5.10 & 6.06 and Xubuntu 6.06 and none of them will use the DNS discovered via DHCP from my Telinudus 1131 ADSL router/modem (192.168.1.1).  Windows XP and other Linux OS' (like ArcLinux and SuSE) have no problem with this.

Moreover, if I select DHCP and manually change the DNS to my ISP's DNS servers, 195.170.0.1 and 195.170.2.2, after 5 - 10 miniutes, Ubuntu or Xubuntu resets it back to the Telinudus 1131 ADSL router/modem's IP address (192.168.1.1).  

I know I could probably solve the problem by switching to a static IP address, but if I recall correctly, even this requires me to use my ISP's DNS servers or I cannot access the Internet.

This sounds to me like a bug.  I should be able to select DHCP and have it just plain ole work, just like it does in Windows XP.

To the developers: If you want to get us off if Windows, you need to make things work right and easy.  I still have faith in you, but I am frustrated with what a pain in the a$$ it is to do anything in any Linux.

---

### Post by fragos on 2006-08-16
I've never had a problem with the DCHP client over a standard Ethernet LAN.  Given the time delay you mentioned its almost as if something is reinitiating the DCHP client server handshake.  Since your modem is a router the DHCP server in play is in the modem.  Most ADSL modems use pppoe and I'n not sure how that impacts the situation.  DCHP protocol is also used betwee the modem and the network to aquire the network IP and DNS.  The DCHP between your PC and modem passes on the DNS IP's and generates a NAT IP for your PC.  Did your ADSL provider give you a PPPOE package to install or did you use the one from the Ubuntu repositories?

---

### Post by ntgooroo on 2006-08-16
The Telindus 1131 ADSL router/modem can use PPPoE or PPPoA, or neither.  Here in Greece every one must use PPPoE or PPPoA.  Thus, I have a user name and password entered into the modem.  This is how the national phone company, OTE, lets you get your ADSL from them and your Internet access from some one else, like Vivodi or Hellas Online.  I get both from OTE.

I have a switch connected to this Telindus 1131 ADSL router/modem.  I currently have 2 Windows XP PCs attached to the switch and they get the DNS (192.168.1.1) from the Telindus 1131 ADSL router/modem and use it all day long every day with no problem.  Same thing when I used other Linux distros, such as SuSE and ARCLinux.  No problem.  I never had these problems with any other OS's.

So, are you suggesting that I may need to install a PPPoE client on my Xubuntu 6.06 laptop?  This does not sound logical given the above.

---

### Post by ntgooroo on 2006-09-03
I am still fighing this.  Does any one have a solution as to how to get Xubuntu & Ubuntu 5.10 & 6.06 to use my router as the DNS and have it actually work?

If not, does any one have a way to make the network settings remember my ISP DNS when I type them in manually?  After a while (5-15 minutes), it forgets and reverts back to my router, which doesn't work in Xubuntu & Ubuntu 5.10 & 6.06.

---

### Post by ntgooroo on 2006-09-04
SOLVED!!!!

Well, it's a workaround, but it solves my problem.

Thanks to this thread:

HOWTO: Router and DNS problems

[http://ubuntuforums.org/showthread.php?t=5690](http://ubuntuforums.org/showthread.php?t=5690)

---

### Post by Claus7 on 2007-05-31
Hello,

Is it possible to tell me how you configured your telindus modem so as to work with ubuntu? The link you are providing doesn't seem to work. 

Thanks in advance!

---

### Post by Claus7 on 2007-06-09
Hello,

my problem is solved. The link is :
[http://ubuntuforums.org/showthread.php?t=336073](http://ubuntuforums.org/showthread.php?t=336073)

Regards!

---

