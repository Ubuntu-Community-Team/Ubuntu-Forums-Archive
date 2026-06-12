---
title: "I have been dumb"
date: 2006-03-04
forum: Desktop Environments
---

### Post by OffHand on 2006-03-04
That's right. Followed the horrible advise on this page: 

[http://www.neowin.net/forum/index.php?showtopic=436125&pid=587239124&st=0&#entry587239124](http://www.neowin.net/forum/index.php?showtopic=436125&pid=587239124&st=0&#entry587239124) 

(I should have looked here instead.)

Is there anyone who know's how I could reverse the steps I took.
I get this error now: 

Cannot launch entry

Details: Failed to execute child process "firefox" (No such file or directory)

I tried to re-install 1.0.7 through the synaptic and official cd but that didn't work  :(
I'm really fond of Firefox so a fix would be great. I just re-installed Ubuntu 3 times so a 4th time wouldn't hurt but I rather avoid it. Thnx in advance.

---

### Post by OffHand on 2006-03-04
Follow up: I managed to install Firefox 1.5.0.1 this way: 

CODE
cd Desktop
sudo cp firefox-1.5.0.1.tar.gz /usr
cd /usr
sudo tar -xzf firefox-1.5.0.1.tar.gz
sudo rm firefox-1.5.0.1.tar.gz

Tried it with:
/usr/firefox/firefox 
and it started.

However when I try to click the firefox icon it doesn't launch and I'm still having a firefox map on my desktop which I cannot move to trash. Not enough permissions to move. Hope this info helps.

---

### Post by OffHand on 2006-03-04
Ok, I made a custom application launch. It seems to be working.
You can close this thread. Thanks.

---

