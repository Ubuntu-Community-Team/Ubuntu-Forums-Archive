---
title: "Google calendar error/Evolution"
date: 2006-06-05
forum: Desktop Environments
---

### Post by plexi50 on 2006-06-05
I have successfully added my Google calendar and a ICS calendar to Evolution and everything loaded and displays. But when I re-open Evolution, both calendars say they cannot resolve the host name. Not sure why, nothing has changed. If I uncheck them they error out as well. Any ideas?

---

### Post by netztier on 2006-09-18
> **plexi50 said:**
> I have successfully added my Google calendar and a ICS calendar to Evolution and everything loaded and displays. But when I re-open Evolution, both calendars say they cannot resolve the host name. Not sure why, nothing has changed. If I uncheck them they error out as well. Any ideas?

Same here; haven't been using Evolution on that particular laptop for a few days, so I can't say when it broke.

The Calendar server does produce a valid file - I downloaded it with wget and imported it to another calendar within evolution - all is there as expected.

But not via "on the web calendars" - Evolution says the hostname is not resolvable - while I am browsing the website on the same server at the same time.

thanks for a hint...

regards

Marc

---

### Post by rigtorp on 2006-11-04
I have the same problem here, strange.

---

### Post by ivotedforkodos on 2007-02-13
I also have the same problem. Sometimes the calendars load with incident, but usually I get a "cannot resolve hostname" error. Any ideas?

---

### Post by jimbz on 2007-02-17
Same problem for me on feisty. Check [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/74070]("https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/74070").

---

### Post by mairabc on 2007-04-23
Hello,

I was having the same problem, because I was pasting the URL from Google with "http://" in the beginning. It seemed to work when I changed the protocol to "webcal://", and keeping all the rest of the URL the same.

Let me know if it works for you.

Best regards =)

---

### Post by skathrein on 2007-09-26
Has anyone resolved this problem.  Changing the "http://" to "webcal://" does not solve the problem for me.  I've also noticed that evolution changes a "%40" that is in the string of characters of my calendar address to "@".  I'm not sure what that's all about.  Any suggestions?

---

### Post by KTQ on 2008-04-05
deleting the http:// did it for me - thanks.

does anyone know if there's a way to make it not read-only?

---

