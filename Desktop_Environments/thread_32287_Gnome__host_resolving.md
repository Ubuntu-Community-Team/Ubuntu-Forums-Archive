---
title: "Gnome | host resolving"
date: 2005-05-06
forum: Desktop Environments
---

### Post by born_confused on 2005-05-06
Well, problems...

STORY
Heres the story. I already had apache installed, and then installed mono-xsp forgetting about apache. Something happened with this that caused my internet to work. I assumed something wrong with /etc/hosts. O:) Dont ask me why I thought this was the case, I was having a problematic day. So anyway, I went about editing /etc/hosts and resolv.conf till I realised by port listening that mono-xsp and apache conflicts were causing problems. I uninstalled mono-xsp, but by then I had already changed the hosts and resolv.conf files. However, connection to the internet worked. I am using wireless and NOT using dhcp to get an address from router. Now on that occasion all was working due to the fact that internet was up. So that night I slept well. 

PROBLEM
Woke up the following machine, turned computer on, and logged into gnome, upon logging in, the screen seemed the freeze  :-? , but actually gnome was opening ridiculously slow as I eventually recieved the following message 

"Could not look up internet address for zed. This will prevent GNOME from working properly". Then something about it may be possible to continue and adding zed to /etc/hosts may fix the problem.

You may have gathered that zed is my hostname. So I added my ip and zed to /etc/hosts and well no it didnt work. Another might problem I noticed is, tha slowness becomes very slow when no network. It is pretty unbearable. So now after all the changes my /etc/hosts file reads

127.0.0.1 localhost.localdomain localhost zed
# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

my /etc/hostname reads 

zed

and my /etc/resolv.conf reads

nameserver xx.xx.xx.xx
nameserver xx.xx.xx.xx

and /etc/host.conf reads

order hosts,bind
multi on

now i get the feeling its because attempting to link my hostname returns no ip
for example 

host localhost returns
localhost has address 127.0.0.1

where as host zed
Host zed not found: 2(SERVFAIL)

and dig zed returns SERVFAIL

Ive checked out the dns addresses, nothing wrong with them, and they shouldnt be causing the problem. Another odd thing is, why does ping localhost take years when no internet.  :-? 

LONG STORY right? Well I tried to be as clear as possible, hopefully someone knows what I may be able to do to resolve this. I thank you in advance,  :-P

---

### Post by crazybill on 2005-05-07
your /etc/hostname is ok
your /etc/hosts.conf is ok

The only error I see is with your  /etc/resolv.conf 
unless  you are using xx.xx.xx.xx in a symbollic fasion. You need a real dns server's ip address, such as 66.17.63.1

To make sure your name resolving is going ok, try this:

ping -c3 [www.cvc.org](www.cvc.org)

---

### Post by born_confused on 2005-05-07
no the dns is a real ip, I already checked it, if theres nothing wrong with all that ... what could it be?

---

### Post by khc on 2005-05-07
My /etc/host.conf reads:
multi off

---

### Post by khc on 2005-05-07
Also I think host only looks at the DNS servers, and not /etc/hosts, so doing 'host zed' will fail, but that's fine. 'man host.conf' states that setting multi to on may cause a performance problem, so you may want to turn it off.

---

### Post by born_confused on 2005-05-07
hmm ok
that doesnt fix the issue. Something is seriously wrong.

---

### Post by bildo on 2005-05-13
I wonder if /etc/hosts should have your hostname "zed" in place of "localhost"

127.0.0.1    zed

---

