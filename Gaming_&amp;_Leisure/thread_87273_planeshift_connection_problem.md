---
title: "planeshift connection problem"
date: 2005-11-07
forum: Gaming &amp; Leisure
---

### Post by madjo on 2005-11-07
I know, I probably should be asking this on the planeshift board, but perhaps the Ubuntu people also know a solution :)

I am trying to play Planeshift. I already downloaded and installed the game, but I have troubles connection to the server.
According to the page [http://laanx.fragnetics.com/](http://laanx.fragnetics.com/) the server is up. But still both the updater and the game tell me "100% fail"... I already added the port (7354) to Firestarter (in case it was the firewall blocking incoming traffic) but that didn't solve it.

Is there some way I can get it to run?

---

### Post by madjo on 2005-11-09
The server is online... but the boards there aren't very helpful. I went back to posts from about 2003 to find an answer and all they said "it is your firewall". Well I turned the firewall off in Firestarter, and it still wouldn't connect.. 

What's more, even with the firewall enabled, it didn't even show up on the 'active connections' list.

---

### Post by Duncan_Idaho on 2005-11-10
same problem here :(

---

### Post by madjo on 2005-11-10
I just got 1 step further...
according to someone on the forum, you should alter the servers.xml file, so that the port number for the fragnetics server reads 7777 instead of 7354...

but the next step will be to upgrade (at least in my case), which is odd, because I used the latest version on their website to install it.
And the updater tells me that I can't use the auto-updater, because my OS isn't supported. Odd little thing... I'm starting to think this game is more trouble than it's worth.

*edit*
interesting, running 'updater -auto' gives me (among others) this message:
> Your updater version is older than the server's..
How the heck do I upgrade then?

*another edit*
In case you want to upgrade to the newer upgrader: check this thread:
[http://www.planeshift3d.com/wbboard/thread.php?boardid=41&threadid=19389&page=1#3](http://www.planeshift3d.com/wbboard/thread.php?boardid=41&threadid=19389&page=1#3)

---

### Post by kb3hkg on 2005-12-19
editing the xml file does seem to work, it worked for me just now, however after updating it says I am using the wrong version of planeshift for the server. No clue what to do about that. Any ideas?

---

