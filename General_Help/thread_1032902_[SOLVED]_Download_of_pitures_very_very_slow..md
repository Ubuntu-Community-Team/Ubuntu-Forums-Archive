---
title: "[SOLVED] Download of pitures very very slow."
date: 2009-01-06
forum: General Help
---

### Post by Camilia on 2009-01-06
I go to a forum and click a link to view a picture. Even after 5 min don't have the full picture. I have the cache set to clear the info after I close firefox.

Is there anything else I can do?

---

### Post by tuxxy on 2009-01-06
Have you tried another browser like Opera to see if the fault lies with Firefox or your connection

---

### Post by Camilia on 2009-01-06
> **tuxxy said:**
> Have you tried another browser like Opera to see if the fault lies with Firefox or your connection

Well, I would if I new how to download Opera. I looked in the synapse and couldn't find it.

---

### Post by Slim Odds on 2009-01-06
> **Camilia said:**
> Well, I would if I new how to download Opera. I looked in the synapse and couldn't find it.

You need to enable the "Third Party" applications (partner) under the repositories.

---

### Post by AlCarmon on 2009-01-06
Camilia
There may be so help here:
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

Warning: lots of pictures, but you can probably figure out the tips before they load.
What kind of internet connection do you have?
Al

---

### Post by Camilia on 2009-01-06
> **Slim Odds said:**
> You need to enable the "Third Party" applications (partner) under the repositories.

I am not quite certain how to do that. 
In the software 3rd party 
Archive.canonical.com/ubuntu hardy partner
Archive.canonical.com/ubuntu hardy partner ( source)
packages.medibuntu.org/ hardy free non free
packages.medibuntu.org/ hardy free non free (source)

Clicked all and closed then something downloaded. Is this safe to do?

---

### Post by Camilia on 2009-01-06
> **AlCarmon said:**
> Camilia
There may be so help here:
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

Warning: lots of pictures, but you can probably figure out the tips before they load.
What kind of internet connection do you have?
Al

Comcast high speed via a modem

---

### Post by tuxxy on 2009-01-06
[http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

---

### Post by Camilia on 2009-01-06
> **tuxxy said:**
> [http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

I don't see hardy, which is what I have. Can I download another version?

I found it.

I am afraid to download it for when I click on a link in my mail I get this message:

Could not initialize the application's security component. The mostly cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behavior when accessing security features.

Does this mean my hard drive is getting full. If so how do I check?

I recently did this:
Type "about:config in the address bar

1.
Alter the entries as follows: 
Set "network.http.pipelining" to "true" 
Set "network.http.proxy.pipelining" to "true" 
Set "network.http.pipelining.maxrequests" to some number like 30. 

2.
Lastly right-click anywhere and select New-> Integer. Name it "nglayout.initialpaint.delay" and set its value to "0". This value is the amount of time the browser waits before it acts on information it receives.

Could this be the cause?  Now I get an error message when trying to sign into flckr.

Well surfing got slower and slower so I did the quick fix. I booted up with the ubuntu CD. Then I couldn't get on line at all. Thus booted up with PC's manufacture CD. Then restarted with ubuntu CD.  I am told that is not wise, but I was uncertain in my attempt to make the entry to true if I had done something in error.

After I get other task finished I am going to check Opera out. Read it is best to get it through ubuntu so that will automatically get the updates.

---

