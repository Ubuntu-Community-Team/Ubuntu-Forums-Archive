---
title: "ADSL connection"
date: 2006-01-11
forum: General Help
---

### Post by KhanArash on 2006-01-11
I have installed Ubuntu 5.10 in my computer, everything are going well, but I have problems with connection to the internet!
I use Online ADSL with username and password and my modem is "CELLPipe" and I would ask you about that if you could help me get connected to internet?

Regards.Arash

---

### Post by manicka on 2006-01-11
What type of problem are you having? Is it just a problem with your browser or a config problem with your modem?

---

### Post by Mr_Grieves on 2006-01-11
First off.. Do NOT publish usernames or passwords to you're systems, if you do not want to risk getting hacked.

Secondly, tell us more about you're connection. Are you connected directly to you're modem? Or via a switch or router? Does the connection use PPPoE? DHCP? Some other kind of login mechanism? Proxies? Have you verified that you are not experiencing some kind of problems due to outage at you're ISP?

Thirdly tell us about you're problem.

---

### Post by KhanArash on 2006-01-11
Secondly, tell us more about you're connection. Are you connected directly to you're modem? Or via a switch or router? Does the connection use PPPoE? DHCP? Some other kind of login mechanism? Proxies? Have you verified that you are not experiencing some kind of problems due to outage at you're ISP?
--------------------------------------------------------------------------

Thnx for your reply...yes i am connected directly to my modem, and the connection use PPPoE. 
I can get connected with windows, but I dont know how to set up the connection for the linux and make it work, since that's first time I am using Linux:)

---

### Post by manicka on 2006-01-11
It may just be that you need to disable ipv6 in Firefox.

Type about:config in the address bar

type ipv6 in the 'filter' field

toggle network.dns.disableIPv6 to 'true'

---

### Post by KhanArash on 2006-01-11
Okei, thnx, but what about the username and password I use to get connected to the Internett with windows? and do I need to active the modem?(I tried to active it,I wrote everything and I did wait 30 minuttes but nothing happened, this would just countinue without giving any result)

---

### Post by drfalkor on 2006-01-11
Correct me if I'm wrong, But I think you're using PPPoE ( or PPoE, can't remember) to connect to the internett .

---

### Post by KhanArash on 2006-01-11
You are right,as I said earlier I am using  PPPoE to connect to the net!

---

### Post by drfalkor on 2006-01-11
Ok then I'ts easy - There should be a progam with a nice GUI there you can write you're username and password, and then Wolla !
Can't remember the name of the program, but it was in Fedora Core ( Gnome ) by default :p

---

### Post by Mr_Grieves on 2006-01-11
PPPoE login can be done via more intelligent modems, is the login done via modem or you're computer?

If it's via you're computer, check this out:
[http://ubuntuguide.org/#rp-pppoe](http://ubuntuguide.org/#rp-pppoe)

Ps.
It's PPPoE (Point to Point Protocol over Ethernet)
Ds.

---

### Post by manicka on 2006-01-11
Have you tried going to Administration-->Networking and configuring the modem there?

---

### Post by manicka on 2006-01-11
also

[http://easylinux.info/wiki/Ubuntu#How_to_configure_broadband_connections](http://easylinux.info/wiki/Ubuntu#How_to_configure_broadband_connections)

may help

---

### Post by manicka on 2006-01-11
also

[http://easylinux.info/wiki/Ubuntu#How_to_configure_broadband_connections](http://easylinux.info/wiki/Ubuntu#How_to_configure_broadband_connections)

may help

---

### Post by Mr_Grieves on 2006-01-11
[QUOTE=manicka]Have you tried going to Administration-->Networking and configuring the modem there?[/QUOTE]
I can't see how an ADSL modem would appear there though :)
It's functioning sepratly from the computer. But perhaps the computers PPPoE functionality, I guess. I never touch the stuff myself :D

---

### Post by drfalkor on 2006-01-11
[QUOTE=Mr_Grieves]I can't see how an ADSL modem would appear there though :)
It's functioning sepratly from the computer.[/QUOTE]

Well, it does :p

EDIT: It dedects my CELLpipe modem there :)

---

### Post by Mr_Grieves on 2006-01-11
Hahaha.. you learn new stuff every day. Hope it works for you :)

---

### Post by KhanArash on 2006-01-11
Re: ADSL connection - 5 Minutes Ago 

--------------------------------------------------------------------------------

Quote:
Originally Posted by Mr_Grieves
I can't see how an ADSL modem would appear there though 
It's functioning sepratly from the computer. 


Well, it does 

EDIT: It dedects my CELLpipe modem there 
 

where?i use CELLpipe modem but I cant find it there?

---

### Post by Mr_Grieves on 2006-01-11
Burn [http://frankandjacq.com/ubuntuguide/rp-pppoe-3.6.tar.gz](http://frankandjacq.com/ubuntuguide/rp-pppoe-3.6.tar.gz) on a CD to get the file to Ubuntu, then follow this guide: [http://ubuntuguide.org/#rp-pppoe](http://ubuntuguide.org/#rp-pppoe)

---

### Post by manicka on 2006-01-11
[QUOTE=Mr_Grieves]Burn [http://frankandjacq.com/ubuntuguide/rp-pppoe-3.6.tar.gz](http://frankandjacq.com/ubuntuguide/rp-pppoe-3.6.tar.gz) on a CD to get the file to Ubuntu, then follow this guide: [http://ubuntuguide.org/#rp-pppoe](http://ubuntuguide.org/#rp-pppoe)[/QUOTE]

This is a hoary guide, will it work in breezy?

The breezy guide has different instructions
[http://easylinux.info/wiki/Ubuntu#How_to_configure_broadband_connections](http://easylinux.info/wiki/Ubuntu#How_to_configure_broadband_connections)

---

