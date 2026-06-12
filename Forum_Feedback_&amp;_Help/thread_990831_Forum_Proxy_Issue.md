---
title: "Forum Proxy Issue"
date: 2008-11-23
forum: Forum Feedback &amp; Help
---

### Post by drubin on 2008-11-23
I know there are 100's of these "the forums aren't working" threads but I have read most of them. This one is slightly different because I got an error message. 

I know there is little the admins can do about it. but thought I would paste the error so maybe they can push it up to the sysadmins.

This was viewing [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39) no post no nothing just pressed enter on the url to re-fresh it.
> 
The proxy server received an invalid response from an upstream server.
The proxy server could not handle the request GET /forumdisplay.php.

Reason: Error reading from remote server

Apache/2.2.8 (Ubuntu) Server at ubuntuforums.org Port 80

Hope this helps you guys,

ps They are clearly working now :)

---

### Post by bapoumba on 2008-11-23
Thanks drubin, also happens to me once in a while :)

---

### Post by drubin on 2008-11-23
> **bapoumba said:**
> Thanks drubin, also happens to me once in a while :)

Pleasure I have never seen this particular error before so though posting the quote would help some one.

ps
Maybe this is the error most people get but just they say "Not working!!!!!" :)

---

### Post by bapoumba on 2008-11-23
I forgot to take a screenshot of the proxy error, will do and post it here next time :)

---

### Post by drubin on 2008-11-23
> **bapoumba said:**
> I forgot to take a screenshot of the proxy error, will do and post it here next time :)

Hopefully there wont be a next time. Maybe that error will get us new servers.(lol)

---

### Post by bapoumba on 2008-11-23
> **drubin said:**
> Hopefully there wont be a next time. Maybe that error will get us new servers.(lol)
We have them already :)

---

### Post by drubin on 2008-11-23
> **bapoumba said:**
> We have them already :)

Must have more! :)

---

### Post by Elfy on 2008-11-23
> We have them alreadyIs it them or is it an it?

Still seem to get forum crashing here - daily occurence - although it's back up quickly usually.

---

### Post by bapoumba on 2008-11-23
> **forestpixie said:**
> Is it them or is it an it?

Still seem to get forum crashing here - daily occurence - although it's back up quickly usually.
Ah, not sure. I remember u-g talking about load balancing, but I'm not sure how we got there (ie, what was added, I'll look).

---

### Post by Elfy on 2008-11-23
Don't worry too much - as the forums grow it's always likely to be a case of catching up I guess :)

Would be nice to know if it's an it or a they - I know there only used to be not enough :D

Always seems to be fine until america wakes up :)

---

### Post by bapoumba on 2008-11-23
> **forestpixie said:**
> Don't worry too much - as the forums grow it's always likely to be a case of catching up I guess :)

Would be nice to know if it's an it or a they - I know there only used to be not enough :D

Always seems to be fine until america wakes up :)

Looks it was one web server added.
I've also noticed that if I browse the forums during my morning (UTC +1), they always run smoothly ;)

---

### Post by Elfy on 2008-11-23
I try to get my forum fix about UTC time and all seems, ahem, as you say much smoother. Must be the Atlantic slowing it down later in the day then :lol:

---

### Post by pp. on 2008-11-23
Right now the forum is throwing fits again.

The proxy message is shown for some requests, others take an unusual length of time, and from time to time the web server responds with 'service temporarily unavailable'.

The proxy message is

> Proxy Error

The proxy server received an invalid response from an upstream server.
The proxy server could not handle the request POST /newreply.php.

Reason: Error reading from remote server

Apache/2.2.8 (Ubuntu) Server at ubuntuforums.org Port 80

POST /newreply.php is for adding a post to a thread. The message is also shown for GET requests, but I haven't bothered to copy those message as well.

It appears that these are all different symptoms for the same problem, i.e. the server being overwhelmed by client requests.

Edit: The POST request which the proxy message refers to has been properly processed. It was just the answer which was not returned to the client.

---

### Post by bapoumba on 2008-11-25
Just got it.

---

### Post by ubuntu-geek on 2008-11-26
The forums are currently running on (1) web servers. The other server in the cluster has been deactivated and we hope to add it back in soon.

---

### Post by Elfy on 2008-11-26
I wondered ;)

---

