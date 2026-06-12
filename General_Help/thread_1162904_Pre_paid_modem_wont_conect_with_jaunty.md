---
title: "Pre paid modem wont conect with jaunty"
date: 2009-05-18
forum: General Help
---

### Post by Bearded-flower on 2009-05-18
Ok, i brought this dodo pre paid wireless modem a few months ago.
With the help of [ this ]("http://ubuntuforums.org/showthread.php?t=1110847&highlight=dodo+modem") thread.
But i just upgraded to jaunty and i tiried the exact same procedure.
changing the apn to dodolns1.
thats all i had to do in intrepid.
it says its conected to the internet, but nothing loades, what gives?
what am i doing wrong.
this is my only means of internet so i need it fixed as soon as possible

---

### Post by Bearded-flower on 2009-05-18
Yeah and as for the thread that was closed before i know im sorry.
i just need it fixed ASAP, sorry about that

---

### Post by Bearded-flower on 2009-05-18
Bump

---

### Post by cariboo on 2009-05-18
Can you ping anything either by ip address or by name? Open a terminal and type:

```
ping 64.233.161.99
```

and see if you get a reply, then try:

```
ping www.google.com
```

If you can ping the numeric addess, but not the url, then you have a dns problem.

---

### Post by Bearded-flower on 2009-05-19
Ok, i tried both, the first the numeric adress Im noy sure wether what it did was normal or not.
it just kept repeating the same messege over and over.
See atached images
and when i tried the adress "www.google.com" nothing, nada, zilch, zippo.
im guessing that means its a DNS problem.
what does that mean?
oh and let me aploagise for my bad engrish.
i dont have firefox so no auto spell check, sorry

---

### Post by cariboo on 2009-05-19
It looks like the issue has something to do with an ipv6 problem. Open firefox and type about:config in the address bar and look fo a line that contains the following:

```
network.dns.disableIPv6 => false
```

and change the **false** to **true**, restart firefox and see if that helps.

---

### Post by Bearded-flower on 2009-05-19
Ok, shall do ill try when i go home

---

### Post by Bearded-flower on 2009-05-20
ARGH!!!!
It didint work
RAWR!!!!

---

### Post by Bearded-flower on 2009-05-20
Oh, added info, the model of the modem is:
Huawei E169, and its on dodo, wich uses the optus network

---

### Post by Bearded-flower on 2009-05-21
Bump

---

### Post by cariboo on 2009-05-21
Could you paste the result of:

```
cat /etc/resolv.conf
```

in your next post.

---

### Post by Bearded-flower on 2009-05-21
Ok ill do it wen i go home.
So do you have any idea whats goin on with it?

---

### Post by Bearded-flower on 2009-05-21
Yeah i not shure if this is right, but here we go.

---

### Post by Bearded-flower on 2009-05-21
bump

---

### Post by cariboo on 2009-05-21
So far we've determined that you are getting an ip address and you can ping by number but not by name. Looking at you screen shot you are getting a dns address from your service provider. Right-click Network Manager and then click Edit connections, highlight you network device and click the edit button, enter your password, then click the ipv4 tab. Make sure you have Method: Automatic (DHCP} set and try to ping a web site by name. 

If that doesn't work set Method to Automatic (DHCP) addresses only and  enter 208.67.222.222 in the DNS Servers. You should be able to connect by name.

---

### Post by Bearded-flower on 2009-05-21
Ok, thanks ill try wen i go home

---

### Post by Bearded-flower on 2009-05-24
Yes! all i had to do was change it to automatic DCHP.
thanks so much.
seriously
thanks.

---

### Post by marshmugger on 2009-06-06
Here are the settings that worked for me, Dodo Wireless Fraudband on my Acer Aspire One with Ubuntu Netbook Remix 9.04.

Create a new connection and select Optus. Then set the following:

 Number: *99#
 APN: dodolns1

 Authentication: CHAP

 DNS: 202.136.43.197, 202.136.42.229

Everything else is default/blank.

I've been waiting a long time to get this work :-) It's my Dad's USB modem, I just steal it and plug it into my netbook.

---

