---
title: "apache2/php5/mysql"
date: 2006-01-14
forum: Desktop Environments
---

### Post by shawnzyoo on 2006-01-14
so this is a strange problem and i am not sure the source of it
i can view my webpages that i created in /var/www/ in firefox on my server
then when i try to view them from another comp on the same LAN
nothing comes up
but when i view the source code
its all there and gets updated
or on other computers (non LAN)
they can view the source also
but not the actual page
please assist
thanks

---

### Post by amohanty on 2006-01-14
That is really wierd. Is the HTML that you can see on the other computers valid, ie not missing any <html> or <body> tags?

AM

---

### Post by shawnzyoo on 2006-01-14
this is the index.html from /var/www
i don't think its missing anything

<html>
<header><title>The Foxhole </header><title>
<body bgcolor="black">
<center> <font size=40 color="#00CC00">Shawns site</font></center>
<center> <font size=10 color="#ff3399"><A HREF="test.html">The GF</A>
<A HREF="http://www.uwm.edu/~aps">my rocket</A>
<A HREF="Alternative.html">Alternative Engineering</A>


</body>

</html>

---

### Post by amohanty on 2006-01-14
What I would try is:
1. restart apache 
2. clear firefox cache
3. hit the url
4. hit the url using lynx
5. hit the url using nautilus

what I am attempting to do is to somehow reproduce the problem on the host server. if there is no way to reproduce it on the host, then the problem does not lie in the server apache/php configuration or usage.

Post the results.
AM

---

### Post by shawnzyoo on 2006-01-15
so i am neophyte to HTML coding
that lynx viewer helped a lot
thanks for the suggestion ( i was totally unaware of such a thing)
my websites are up now. so once again thank you

---

### Post by amohanty on 2006-01-15
so i am guessing you dfound out that these
> <header><title>The Foxhole </header><title>
> font size=10 color="#ff3399"><A HREF="test.html">The GF</A>
were the problem. :)
Try using NVu (its in the repos) for HTML editing. It has a validate tool which wil validate your html.

HTH
AM

---

