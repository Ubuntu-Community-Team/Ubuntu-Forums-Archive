---
title: "Firefox won't connect locally, Konquerer will!!"
date: 2006-05-21
forum: Desktop Environments
---

### Post by rnfuller on 2006-05-21
I have a weird problem going on I can't seem to figure out.  I just did a fresh install of Dapper Kubuntu on my laptop.  I have a Breezy system setup on my network as a server that runs Apache that I use for a Intranet Server and for development.  When I try to go to my local webpage on my laptop, It fails to connect.  I can't get to Webmin on the server either.  But if I try the same thing using Konqueror instead of Firefox, it works fine!

I have no proxy settings in Firefox and I can access Internet sites fine.  I am at a loss as to what is going on.  Anybody have any suggestions?

Thanks
Randy


[B]SOLVED!
Remove all mozilla stuff with Adept and then re-installed.  Apt-get remove and install just did firefox and left other stuff behind.[/B]

---

### Post by DeadCD on 2006-05-22
hmm i suggest reinstalling firefox or just reinstall your whole system meh

---

### Post by rnfuller on 2006-05-22
I tried, *sudo apt-get remove firefox* and then *sudo apt-get install firefox*

No change.  Firefox will go to [www.google.com](www.google.com) or any internet site fine, but if I type [http://192.0.168.3](http://192.0.168.3)  it chokes with a Failed to connect to Web Server error.

Randy

---

### Post by lotusvball on 2006-11-10
I am having similar issues with access my website on my local network.  When I am at work everything is fine but when I try to log on when I am on the local machine or my local network it takes forever.

---

