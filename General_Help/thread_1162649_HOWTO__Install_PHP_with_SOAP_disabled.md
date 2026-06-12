---
title: "HOWTO : Install PHP with SOAP disabled"
date: 2009-05-17
forum: General Help
---

### Post by tsuriken on 2009-05-17
):P Hi all

i'm newbie member here on ubuntu forum, this is my first post

i'm Ari from Indonesia, glad to see you here :p

sorry for my bad english..


 i wanna ask to all ubuntu masters here

i want to install PHP on my ubuntu Jaunty Jackalope, without SOAP (soap disabled), it is very important for my program in webservices using nusoap..

i'm already find the result about this problem on this forum [here]("http://ubuntuforums.org/showthread.php?t=497460"), but it's doesn't work for me at all

can anyone give me a hand to solve this problem??
i'm very appreciate for your answers..

best regards,
ARI

---

### Post by frodon on 2009-05-18
Moved to general help

---

### Post by tsuriken on 2009-05-18
Thank you to move my thread..
sorry i'm newbie here

anyone can help me??

---

### Post by tsuriken on 2009-05-19
Hi all, if u r find the same issue like me

definitely, i had try all things to disable SOAP in PHP but i can't solve this problem

and now i can fix my trouble using this NuSoap version ==> [NuSoap]("http://webscripts.softpedia.com/script/Development-Scripts-js/nusoap-for-php5-30663.html")

all you need is to download this NuSoap version and change name of your soapclient in your nusoapclient.php to soapclientNusoap

example : ($client = new [COLOR=Blue]soapclient[/COLOR]  ==> $client = new [COLOR=Blue]soapclientNusoap[/COLOR])

just that's

regards,

Alternatively, this is the way if you can't disable your SOAP in PHP :)

Thank you

---

