---
title: "protect myself from crackers"
date: 2009-06-09
forum: General Help
---

### Post by themacedonian on 2009-06-09
We know that in our planet have more and more crackers, not hackers. 
Me and other who using ubuntu want protect and be safely while siting on his/her pc. 
So, what is best way for protect ?
I have changed my ssh port, any diferent idea ? i think that changing ssh port its not enought ...

---

### Post by R33D3M33R on 2009-06-09
Use a firewall. For example Firestarter.

---

### Post by H2SO_four on 2009-06-09
Ubuntu has built in firewall, btw

---

### Post by sedawk on 2009-06-09
A cracker is someone who removes copy protection from commercial
software. A hacker is someone using data networks like the internet
to hack into your computer.

What is the name of people running malicious web sites to attack
your computer - aren't they hackers too?

Anyway, your computer is well protected if you regulary install
security updates and do not install suspicious software or
visit suspicious web sites (see "adblock plus" plugin for firefox
and "noscript" plugin to improve web security).

The only safe way to connect a computer to the internet only via a DSL
modem (not via a DSL router with built-in firewall) is to run Linux on
that computer. 

Changing ports is no good protection. Anyway ssh with a good password
or ssh limited to a small list of known "authorized keys" is very
secure. 
But if you think you have to improve security (e.g. "hide ssh port") you
can try "knock". E.g. ssh is only activated if you knock on the
correct door (port) and say the right password ...

---

### Post by Celauran on 2009-06-09
> **themacedonian said:**
> i think that changing ssh port its not enought ...

Disable password logins for SSH, restrict access to certain usernames, and/or restrict access to certain IP addresses.

---

### Post by oldsoundguy on 2009-06-09
find out which ports are open (if any)

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by Hund on 2009-06-09
Desktop or server? What services are you running?

---

### Post by themacedonian on 2009-06-10
i am using ubuntu desktop edition.
btw, how i could view if somebody is conected with ssh in my pc ? 
for example, my brother has conect sometimes from other pc but i dont know 

thanks

---

### Post by Legace on 2009-06-10
Get a router with built-in NAT and SPI.

---

### Post by Therion on 2009-06-10
I was once assaulted by a cracker.





/rimshot

---

### Post by Soul-Sing on 2009-06-10
themacedonian are you behind a router?

---

### Post by Grenage on 2009-06-10
> **sedawk said:**
> A cracker is someone who removes copy protection from commercial
software. A hacker is someone using data networks like the internet
to hack into your computer.


That's really just not right,

---

### Post by Celauran on 2009-06-10
> **themacedonian said:**
> btw, how i could view if somebody is conected with ssh in my pc ? 
The command 'who' will show you who is logged in at any given time.

---

### Post by themacedonian on 2009-06-10
> **leoquant said:**
> themacedonian are you behind a router?

nope.
i am directly conected with motorola cable modem. 
i want to be sure that my documents are safely while my computer working :)

thanks

---

### Post by Celauran on 2009-06-10
```
man iptables
```

---

### Post by CrazyMonkeyFox on 2009-06-10
> **Grenage said:**
> That's really just not right,

Ye he's right, crackers by definition are what you perceived as hackers with malicious intent. Hackers are those that see the option to exploit, etc. and inform webmasters or whatever. There's several articles on the web that discuss this, that try and seperate themselves from the media's view of 'hackers'.


__________
CrazyMonkeyFox

---

### Post by Hund on 2009-06-10
> **themacedonian said:**
> i am using ubuntu desktop edition.
btw, how i could view if somebody is conected with ssh in my pc ? 
for example, my brother has conect sometimes from other pc but i dont know 

thanks

"users" shows the current users.

Some good reading: [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by Soul-Sing on 2009-06-10
> **themacedonian said:**
> nope.
i am directly conected with motorola cable modem. 
i want to be sure that my documents are safely while my computer working :)

thanks

You could enable a frontend for iptables as firestarter or GUFW.
Or take some time and study iptables.
Remember Ubuntu has a zero open ports policy.
You can "stress" your system with a portscantest at: "shields-up¨.
: [http://www.grc.com/intro.htm](http://www.grc.com/intro.htm)

---

### Post by michy99 on 2009-06-10
I have found that the only way to get rid of crackers is to take the sheets off the bed and wash them.

---

### Post by balloooza on 2009-06-10
> i am directly conected with motorola cable modem. 
Yikes, but wait, you are using ssh over the internet, that is even more "yikes" ish to me, I only use vpn over the net, with some intense security, and I have a firewall.
Secondly, I not only open ONLY the ports to the internet neccecary, I tuned my network so that even certain communication *within* my network is restricted, but be warned, if you are forgetfull you will be trying for hours to get pulse to stream over the network. (LOL, I JUST WAS DOING THAT, I GAVE UP YESTERDAY, I just realized that)

But look at that conficker virus for windows, it used the internel network to communicate between windows machines, this setup will protect from that too.

Security is somthing that you should invest in, if you do onlne banking or purchasing, "Crackers" (I didn't know the world was to the point that different types of hackers got different names) Can literly get access to anything that they want, They can see the data whip through the net (try wireshark, you would be amazed how much you can see happening)
My best advice, is (at least you have to trust the site) but make sure that the page is all Secure when you are doing somthing with money, by pressing the logo in firefox next to the url, it will tell you somthing reassring.

---

### Post by hibliss on 2009-06-10
Buying a router, specifically a Linksys WRT54G/GS and installing either DD-WRT or Sveasoft will give you a lot more security, and instead of ssh direct to the port, you can setup a VPN connection direct to the Router that requires a password, then ssh or vnc to the machine, whichever you prefer. 

That is my suggestion, get a router with a hardware firewall.

---

