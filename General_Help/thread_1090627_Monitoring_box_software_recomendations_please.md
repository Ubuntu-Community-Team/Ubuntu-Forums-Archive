---
title: "Monitoring box software recomendations please"
date: 2009-03-08
forum: General Help
---

### Post by computergroove on 2009-03-08
I have a house full of children and I need to administer some control over what is being done on my local area network. I want to do a few things. First I want to monitor all the websites that are being browsed on my network.

The Setup:
I have a Linksys router with DDWrt installed. I have a DSL modem. I have 6 computers on my home network. All the computers are running XP Pro. some are wireless and some aren't. 

What I want to do is setup a Ubuntu box that monitors all the lan/wan traffic and stores the data for future look ups. I want to view the computer name and the website visited (cached if possible so I can just see what was viewed) and I want to be able to filter what content is able to be viewed (based on web site names and words found in the URL or in the website content. I also have 1 printer on my network that everyone uses and I want the printer to be shared on the ubuntu box but I want to cache all the documents being printed and be able to view them on the screen. What utilities can I use to get this done? The printer is a HP Laserjet 5. Thanks in advance.

---

### Post by kestrel1 on 2009-03-08
I am sure it is possible to setup ubuntu to do all of this, but you could look at K9 webfiltering software: [http://www1.k9webprotection.com/](http://www1.k9webprotection.com/)
the only down side is you would need to install this on each machine & you would need a separate licence for each machine. These are normally free for a single machine, but you could ask the manufacturers if you could install on all the machines.
I expect others will come up with a better solution in Ubuntu though. Not in my field of expertise.

---

### Post by computergroove on 2009-03-08
Thanks for the link but it doesn't fill all of my requirements. I found this for the monitoring but it doesnt fill the requirement about print caching - [http://www.geek.com/articles/chips/feature-buiding-a-mini-itx-web-content-filter-with-ubuntu-20090116/](http://www.geek.com/articles/chips/feature-buiding-a-mini-itx-web-content-filter-with-ubuntu-20090116/)

---

### Post by kestrel1 on 2009-03-08
Not sure if this will help with regard to your printer needs, but you can view certain things about your attached CUPS printers with the following```
http://localhost:631/
```

---

