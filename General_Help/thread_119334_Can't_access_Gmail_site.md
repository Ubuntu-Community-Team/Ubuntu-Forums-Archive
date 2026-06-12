---
title: "Can't access Gmail site"
date: 2006-01-19
forum: General Help
---

### Post by zachariah on 2006-01-19
Everything else I can think of is working. I can see pretty much any other website you care to mention. I can browse network shares. But for some reason when I try and go to gmail.google.com, Firefox (and Konqueror) just hang and eventually declare that the document contains no data. 

Any ideas?

Breezy 5.10 with all updates, Firefox 1.5

---

### Post by cblanquer on 2006-01-19
Have you tried [www.gmail.com](www.gmail.com) ?  :smile:

---

### Post by linbetwin on 2006-01-19
It's mail.google.com/

---

### Post by zachariah on 2006-01-19
Unfortunately neither of those alternatives work...Firefox (and Konqeror) just hang indefinitely.

I'm fairly certain it's not a firewall issue. The Linux box is allowed to send/receive anything. Other computers on the network are able to see the gmail page (at the address I mentioned and the ones you provided).

All other websites and internet protocols appear to be working fine, synaptic, etc.

---

### Post by Grim76 on 2006-01-19
try [https://mail.google.com/mail](https://mail.google.com/mail)

That is what I use to get there.

---

### Post by Minyaliel on 2006-01-19
I had the same problem, and had to swap browser - now that I use Mozilla, its no problem anymore.

---

### Post by zachariah on 2006-01-23
Update - the problem seems to be a general inability to access HTTPS sites. Any browser (including Mozilla), when trying to open any HTTPS site, just waits for a few minutes then times out. 

I've used Ethereal to have a look at the traffic but I'm no network guru so it hasn't helped much. From what I can understand, Kubuntu is initiating the HTTPS request and has no problem with DNS, but the HTTPS negotiation is just not completing.

This is really annoying, as not only Gmail but the Ubuntu Wiki is HTTPS...as are several other web sites I'd like to visit...ahem...anyway. Any ideas?

---

### Post by carl13 on 2006-01-23
[QUOTE=zachariah]Unfortunately neither of those alternatives work...Firefox (and Konqeror) just hang indefinitely.

I'm fairly certain it's not a firewall issue. The Linux box is allowed to send/receive anything. Other computers on the network are able to see the gmail page (at the address I mentioned and the ones you provided).

All other websites and internet protocols appear to be working fine, synaptic, etc.[/QUOTE]

Are you trying to access it from work? If so, this is probably not news for you, but many companies block access to web based email sites. The company that I work for blocks access to many sites. Some hang up as you mentioned and others have a page that pops up and states that access is not allowed.

---

### Post by zachariah on 2006-01-24
I am trying this at work, but the annoying thing is that all the Windows boxes have no problem going to any HTTPS site, including Gmail. They're in the same room, going through the same switches, the same servers....

Bit of a mystery really.

Static IP - all subnets, gateways, DNS servers etc are correct (insofar as they allow all other internet communication, can ping internal and external computers). 

Internet access is through a MS ISA server. There is a protocol rule to allow all IP traffic from the static IP reserved for the Kubuntu box (I also put a separate rule to allow HTTPS through, though this should not be necessary - no joy).

---

### Post by wanger123 on 2006-01-24
Hi there, I assume you have done the obvious and setup the konqueror proxy settings for http, https, and ftp???

wanger

---

### Post by zachariah on 2006-01-24
I'll be darned! After all that, wanger123 successfully realises I've missed the bleeding obvious!

Thankyou!

I just *knew* it was something simple, staring me in the face...sigh...

---

### Post by wanger123 on 2006-01-24
No probs, glad to be able to help someone else after all the assistance I've received from these forums
wanger

---

### Post by cblanquer on 2006-01-24
Zachariah

The best way is to identify other URLs you are not able to access form Ubuntu-PC but reachable from the other ones or any other exception case, in order to identify the pattern that does not allow you to reach gmail.

Alternatively, check if you are allowed, the firewall policies at the MS ISA server (if there were any). You may have all IP traffic apparently authorised and have naother parameter filtering the access to gmail URLs.
(I use a 3Com ADSL router and some mistakes in the firewall rules  made me not being able to access some servers because I had some ports not allowed for instance.)

I hope this helps.

---

