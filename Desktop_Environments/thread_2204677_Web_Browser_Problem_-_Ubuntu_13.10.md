---
title: "Web Browser Problem - Ubuntu 13.10"
date: 2014-02-09
forum: Desktop Environments
---

### Post by matrixmysql on 2014-02-09
Okay this is a huge issue I'm having with my browsers in Ubuntu. (This issue doesn't seem to happen in Windows). I'm coming off a relatively fresh install and I'm having the same issue on both Firefox and Chromium. 

Here is the issue:

I will just be casually surfing the web until my browser randomly redirects me to my homepage on that current tab. Sometimes it keeps doing it over and over again making surfing the web impossible. It seems to be acting at random too. Sometimes I have no hands on the keyboard, and it still will do it.

My attempts at a solution:

First, I thought it may be a browser extension going out of wack, so I disabled AdBlock Plus and NoScripts and launched in "safe mode." It didn't matter, I still had the issue.
Then, I thought it may be some weird network error. However, I disconnected my computer from the internet, but it was still trying to refresh the tab despite being disconnected.
Most recently, I launched xev on my Firefox browser to see what is going on. Voilà! After twenty or so minutes surfing the web, my webpage randomly went back home. Xev said it was sent a KeyPress command of keycode 180. Now, I don't even know if I have a key that corresponds with this code. I don't think it is an issue where a key is stuck either because then the issue should be apparent in my Windows 7 partition.

Please help me!

---

### Post by matrixmysql on 2014-02-09
Okay, I found a the key that corresponds with keycode 180 (it is an obscure web launcher key by my power button that I've never noticed). I've gone ahead and typed the command:

xmodmap -e 'keycode **180** = NoSymbol'

Going to see if this solves my problem.

---

### Post by matrixmysql on 2014-02-11
Okay, the problem is not fixed.

  Today my computer went crazy and must of sent enough requests to get by this command? My fan turned on because of how many times the keyPress 180 was sent over and over again. I had to restart for the fan to go back to normal and the requests to stop.   

Please post advice to help fix this!

---

