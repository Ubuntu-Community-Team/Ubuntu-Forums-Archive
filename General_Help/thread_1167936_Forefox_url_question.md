---
title: "Forefox url question"
date: 2009-05-23
forum: General Help
---

### Post by Cowchip7 on 2009-05-23
When I used to run firefox on windows and mac, I could just type "google" or "digg" in the url box and hit enter. Firefox would automatically pick the correct .whatever and direct me to the site.

Currently, when I type "google" and hit enter, I get directed to this url: [http://wwwwz.websearch.verizon](http://wwwwz.websearch.verizon)........... etc. url.

What's the deal?

Thanks guys!

---

### Post by zero777zero on 2009-05-23
my ubuntu doesnt do that. what is your default seach engine choice?

---

### Post by cariboo on 2009-05-23
Sounds like you have allowed your browser to be hijacked. Could you post the output of:

```
cat /etc/resolv.conf
```

The above command must be run in a n Applications-->Accessories-->Terminal.

---

### Post by Cowchip7 on 2009-05-23
nameserver 192.168.1.1

---

### Post by Cowchip7 on 2009-05-23
I googled the verizon url and found an archived ubuntu post that gave me some insight (see below). Currently, I am surfing the web in a coffee shop. I will have to try this again on my Comcast connection. Since I haven't noticed this problem before, it probably has something to do with the the Verizon ISP.


About the Search Results Page

You reached the preceding search results page because Verizon is using specific Domain Name Service (DNS) Servers to look up domain names. These DNS Servers eliminate dead-end "no such name" error pages you can encounter as you surf the web. This search service is designed to make your web surfing experience more productive. No software was installed on your computer for this service to work.

• What is DNS
All Web sites have an address that consists of a series of numbers separated by periods, such as 153.39.1.1. This is known as an IP address. Most Web sites also have a domain name (such as [www.verizon.net](www.verizon.net)) associated with their IP address. With DNS, users don't have to type the complicated IP address into their browser's address bar; instead, they can type the domain name. DNS then acts like a real-time phonebook, looking up the name entered and translating it into the numbers that the computer recognizes so that the desired Web site can be displayed.

---

### Post by lovinglinux on 2009-05-23
Is just the ISP search engine, showed when it can't find the web site. I have a similar service on my ISP. I hate it, but there is nothing to worry about.

---

### Post by Cowchip7 on 2009-05-23
Yep. Everything is back to normal on my comcast connection.

---

### Post by ALIENDUDE5300 on 2009-05-23
I'm on a Verizon FiOS Connection @ 15mbps and I don't have any problems whatsoever. When I type google and digg in the search bar, I am directed to the respective sites.

---

