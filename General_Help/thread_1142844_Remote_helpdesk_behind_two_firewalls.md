---
title: "Remote helpdesk behind two firewalls"
date: 2009-04-29
forum: General Help
---

### Post by Oceanwatcher on 2009-04-29
Here is the scenario:

I am running Kubuntu 9.04 and have installed it for a couple of friends. They need help, but it is a hassle to have to get out and go there each time. So I am trying to find a way to do this remotely. We only have two problems:

Firewalls.

Each of us have a router that is supplied by the ISP and that we do not have access to. It is running NAT and a small firewall. This means we can not set up any routing or ports that allow us to go from one to the other.

So we need a "middle man" solution. Something that allow me to connect to my friend to help him.

Before anyone say "Change ISP" - there are no others here! Complete monopoly... I am living in the mountains between Sao Paulo and Rio de Janeiro and the speed is not good...

A good way to do this would be to use Kopete (or Pidgin in Ubuntu) to set up the connection. I think that Jabber could handle this using the same system as Jingle is using. This would be a good project to do and could help spreading Ubuntu/Kubuntu/Linux even more!

---

### Post by Bindsa on 2009-04-29
Have you tried forwarding your ports to your computer? (If not do it by typing the IP of your router into your browser, if everything is OK a graphical interface should show op).

---

### Post by lovinglinux on 2009-04-29
You could use something like "[LogMeIn](https://secure.logmein.com/home.asp?lang=en)", but I don't know if it works on wine.

I used this type of service before on Windows. There are a few more like this out there, that acts like a middleman. I'm not sure about the security tho.

BTW, I understand your problem with the ISP. Where do you live? Campos do Jordão? Santo Antônio do Pinhal?

---

### Post by Oceanwatcher on 2009-04-29
> **Bindsa said:**
> Have you tried forwarding your ports to your computer? (If not do it by typing the IP of your router into your browser, if everything is OK a graphical interface should show op).

Ehrrm...

> 
Each of us have a router that is supplied by the ISP and that we do not have access to. It is running NAT and a small firewall. This means we can not set up any routing or ports that allow us to go from one to the other.

I am sure you overlooked this section just by accident :lolflag:

---

### Post by tommynz1975 on 2009-04-29
what brand is your router/modem as its features might just be hiden to you, ones your isp has not told you exist...  the community might even be able to help you telnet into your router and access more features.

---

### Post by Oceanwatcher on 2009-04-29
> **lovinglinux said:**
> You could use something like "[LogMeIn](https://secure.logmein.com/home.asp?lang=en)", but I don't know if it works on wine.

I used this type of service before on Windows. There are a few more like this out there, that acts like a middleman. I'm not sure about the security tho.

BTW, I understand your problem with the ISP. Where do you live? Campos do Jordão? Santo Antônio do Pinhal?

I have tried researching some of these services, but so far I have not found any that can handle Linux at both ends. One thing that was encouraging though is that I found a project on Sourceforge that was thinking about using Jabber as the "middle man". This is exactly what I was thinking about. Then we could just have another button in a chat window (by a plugin) where my friend could click and "Ask for remote support".

I live in Delfim Moreira, Minas Gerais. It is in the mountains between Sao Paulo and Rio de Janeiro. Internet is through wireless and we have about 200kb down and 64 kb up. Not much to work with, but better than having to drive 30 minutes more up into the mountains to do a small fix. It is far from where I was born in Norway in many senses... :-)

---

### Post by Oceanwatcher on 2009-04-29
> **tommynz1975 said:**
> what brand is your router/modem as its features might just be hiden to you, ones your isp has not told you exist...  the community might even be able to help you telnet into your router and access more features.

You mean the no-brand board that is in that anonymous plastic box? Just to be very clear:

There is no access to this at all. Nada. Zip. I don't even want to try it. If I do, it is easy to find out, and I will be without internet connection. As I mentioned, there is no alternative here, so it is not even worth spending energy thinking about it :-)

---

### Post by poundjd on 2009-04-29
> **Oceanwatcher said:**
> You mean the no-brand board that is in that anonymous plastic box? Just to be very clear:

There is no access to this at all. Nada. Zip. I don't even want to try it. If I do, it is easy to find out, and I will be without internet connection. As I mentioned, there is no alternative here, so it is not even worth spending energy thinking about it :-)
Have you tried getting DynDNS and then doing port forwaring on the two routers from the domain names that you got from DynDNS?  this might work for you.
-jeff

---

### Post by Oceanwatcher on 2009-04-30
> **poundjd said:**
> Have you tried getting DynDNS and then doing port forwaring on the two routers from the domain names that you got from DynDNS?  this might work for you.
-jeff

You mean the routers that we can not, under no circumstance get access to? Please read this again. No portforwarding possible.

To put this in even clearer terms:

From my computer, the request has to go OUT. Nothing can come in. From my friends computer, the request has to go OUT. Nothing can come in.

This is in essence how IM works even when both are behind heavy firewalls. They use a middle-man to take care of the connection.

I appreciate that the suggestions might be sincere, but read the messages again people. There are no ways to initiate any traffic in. It HAS to go out. This is exactly why it is so difficult. As soon as I have a router I can control my self, I will have no problem setting this up. But it can take years before that happen.

---

### Post by lovinglinux on 2009-04-30
Basically the problem is that the OP can't port-forward. The only broadband service available in his area is via wireless, so the router is in the ISP office and he doesn't have administrative access to the router. This might sound weird for most people, but that's what it is.

So, the only way he has to connect to other machine is to use a middle-man service/software, so both machines will be initiating the connection request to the middle-man server. Once each machine connects to the server, it will be allowed to send data back and forward between both machines. This would not require port-forwarding.

---

### Post by Oceanwatcher on 2009-04-30
Thank you, lovinlinux. This is probably how I should have put it myself :-)

---

