---
title: "href links in websites not redirecting on internet"
date: 2010-12-08
forum: Desktop Environments
---

### Post by nishikantu on 2010-12-08
hi,

I have installed ubuntu 10.10  and have installed apache2. also have got the website i meant to start up and running on the default index.html itself and is working perfectly on the locally as well as internet.

Now here is the issue....the hyperlinks that have been mentioned in the html pages are pointing to the private IP addresses of the servers and switches. Now with everything up and running ...locally sites works happily. But when tried over internet , these hyperlinks are not redirecting to the said locations....due to private IPs mentioned in the href.

Now how to resolve the issue and get the thing working.

please help....sitting on a time bomb..

---

### Post by photoben on 2010-12-08
Is there any sort of CMS, or are you coding the pages by hand? Are they static or dynamic?

I'm reading your post as "I want to make the website(s) viewable internally on the LAN and also on the internet." Is this correct?

If so, I would say make everything use domain names (as in public domain names), perhaps using /etc/hosts to redirect locally for speed...would this not work for your setup?

---

### Post by nishikantu on 2010-12-08
Thanks for the response.


i am designing a static page.

The website is completely accessing in the local LAN. But the web page consists of "href" pointing to other webservers in LAN . For this i have used IP address in href 

(example href="192.168.10.20")

with this the link redirection is working on LAN, but due to private IP used, when the site is accessed on internet..the same link is not redirecting due to private IP.

Please assist.

---

### Post by photoben on 2010-12-08
It's pretty simple—you cannot use private IP addresses on the internet, and have them be addressed to your local LAN. It just doesn't work that way.

What exactly are you trying to set up, and do the machines have public IP's?

---

