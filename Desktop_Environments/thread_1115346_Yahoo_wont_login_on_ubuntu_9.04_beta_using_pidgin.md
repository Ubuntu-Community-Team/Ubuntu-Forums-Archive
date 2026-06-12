---
title: "Yahoo wont login on ubuntu 9.04 beta using pidgin"
date: 2009-04-03
forum: Desktop Environments
---

### Post by Wanas on 2009-04-03
I have just installed ubuntu 9.04 beta its great and really perfect but its not 100% okay, one of the things that I have met is the yahoo not working on pidgin, I have tried other protocols like msn it works great but yahoo wont login at all I have tried my other yahoo account but the same results :(.

---

### Post by theraje on 2009-04-06
Are you getting the "Connection Refused" notification? If so, I suspect it's Pidgin or the Yahoo! Network itself, as it does this for me on Windows XP after I upgraded to Pidgin 2.5.5.

---

### Post by Wanas on 2009-04-07
The problem is that I have tried to use empathy but the same results (hotmail works yahoo not) :(

---

### Post by Famke on 2009-04-07
i have checked it’s really great

---

### Post by jugolam on 2009-04-07
same problem here!

---

### Post by Wanas on 2009-04-10
this is my debug window while trying to connect to yahoo

```
(15:24:55) util: Writing file prefs.xml to directory /home/wanas/.purple
(15:24:55) util: Writing file /home/wanas/.purple/prefs.xml
(15:26:25) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(15:26:25) dbus: The signal "gtkblist-hiding" caused some dbus error. (If you are not a developer, please ignore this message.)
(15:26:25) prefs: /pidgin/blist/list_visible changed, scheduling save.
(15:26:31) util: Writing file prefs.xml to directory /home/wanas/.purple
(15:26:31) util: Writing file /home/wanas/.purple/prefs.xml
(15:27:23) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(15:27:23) dbus: The signal "gtkblist-unhiding" caused some dbus error. (If you are not a developer, please ignore this message.)
(15:27:23) prefs: /pidgin/blist/list_visible changed, scheduling save.
(15:27:29) util: Writing file prefs.xml to directory /home/wanas/.purple
(15:27:29) util: Writing file /home/wanas/.purple/prefs.xml
```

and this appear on the pidgin window 
```
Could not establish a connection with the server:
Connection timed out
```

---

### Post by Wanas on 2009-04-12
and when I try to use the web messenger like iloveim.com yahoo works great, any suggestions will be great

---

### Post by Wanas on 2009-04-12
and today I have installed kopete and I have tried yahoo and msn, yahoo didnt work but msn works great :(

can any body help me because I have get fedup from this ](*,)

---

### Post by Wanas on 2009-04-16
This can be fixed by changing the port from 5050 to 20

---

### Post by monstrosity on 2009-04-19
Changing the port to 20 does not fix it for me.

---

### Post by monstrosity on 2009-04-19
Ok, I fixed the problem. I started a new yahoo account, found that it did connect, then opened up both edit-account gui's. In there, I found that my original account was connecting to the wrong server. I copied the information from the new account settings over and it worked like a charm. I did not need to connect to a different port. 

I think sometime in the past, I changed it so I could have some sort of additional functionality.

---

### Post by cfeagans on 2009-04-21
What's the correct server? I've tried a variety of "fixes" including the port change and using the ip address instead of the DNS but I still get the "connection refused" notification. In the last two days, I've been getting this error, though it did connect briefly this morning.

---

### Post by stilling on 2009-04-21
> **cfeagans said:**
> What's the correct server? I've tried a variety of "fixes" including the port change and using the ip address instead of the DNS but I still get the "connection refused" notification. In the last two days, I've been getting this error, though it did connect briefly this morning.

just try scs.msg.yahoo.com port 5050 
and if you want something like a yahoo messenger for windows try Gyachi you will like it

---

