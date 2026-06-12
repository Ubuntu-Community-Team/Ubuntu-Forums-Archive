---
title: "Firestarter IP Range"
date: 2006-09-21
forum: Desktop Environments
---

### Post by chucksaysword on 2006-09-21
Hi all,

I have an issue dealing with Firestarter and IP ranges. I would like to configure Firestarter to allow service to a wide range of IPs. Ideally, I would like to allow service to every IP that starts with 154.123. I know that I can use something like 154.123.214.1/24 to allow service to IPs from 154.123.214.1 - 154.123.214.254, but I want to allow service to anything that has an IP starting with 154.123. If that is not possible, is it possible to allow service to a range of hostnames? i.e. allow service to *.people.company.net. Any help in solving this would be greatly appreciated. I am new to Ubuntu, but I have been using Linux for at least 5 years. I am not too network-savvy, but have a good knowledge of the basics.

---

### Post by skymt on 2006-09-21
154.123.214.1/16 should work. See [Wikipedia](http://en.wikipedia.org/wiki/Netmask#Subnetworking_concept) for why.

---

### Post by chucksaysword on 2006-09-21
Thank you for the link and advice. However, it did not entirely solve my problem. Using the address 154.123.1.1/16 made it so that any client with an IP starting with 154.123. could use the service on the firestarter computer. Problem Solved!

---

