---
title: "Quake live (firefox crash)"
date: 2010-11-26
forum: Gaming &amp; Leisure
---

### Post by karogi on 2010-11-26
After some updates, firefox got crash when i tried to play quake live. where wasn't any error 1week ago. 

Anyone know what happened?

---

### Post by chirag64 on 2010-11-26
It says on the website

[COLOR="Red"]**Support for Mac & Linux, along with alternative browsers is under development.**[/COLOR]

So, clearly they aren't supporting Ubuntu Firefox yet :(

---

### Post by karogi on 2010-11-26
So, can you explain for me. Why I didn't have any problems 1weeks ago to play it?

---

### Post by chirag64 on 2010-11-26
It is quite possible that they made some changes that maybe working for your Firefox earlier, but not now.

You can still try to clear Firefox's cache and cookies and again give it a try.

---

### Post by WienerWuerstel on 2010-11-26
I tried it just now and it crashed for me too.

It could be because you run a Daily Build Firefox or a Quake Live Update broke something.

But it isn't because of missing Support for Linux. 

Quake Live supports Windows, Mac , Linux...

---

### Post by karogi on 2010-11-26
few days ago and today, update manager suggested for me to update my system and i did it. but it looks that it damaged something for firefox (to launch quake).

---

### Post by karogi on 2010-11-26
I solved the problem.



1. Get Greasemonkey: [https://addons.mozilla.org/en-US/firefox/addon/748/](https://addons.mozilla.org/en-US/firefox/addon/748/)
2. Tools -> Greasemonkey -> New User Script
3. Enter a name, namespace (I used "quakelive_fix" as I had no clue) and  in Includes the address for the Quake Live page where you launch the  game ([http://www.quakelive.com*]("http://www.quakelive.com*/")). 
4. Click OK and choose your text editor. I chose /usr/bin/kate but it can probably be anything you like. 
5. Under the "// ==/UserScript==" line add: window.location = "javascript:void(quakelive.siteConfig.videoService  ='ololo')"

---

### Post by WienerWuerstel on 2010-11-26
Glad too see that you solved the Problem and thanks for posting the Solution because it can help those who have the Problem too.

---

### Post by frenzie on 2010-11-29
tried the greasemonkey fix, but didnt work for me :(

---

### Post by peacewithall on 2010-11-30
It doe's work, but you have to make sure you set the window to 'full screen', within the website's game settings, sometimes the setting might not take on the first try, I had to go back and set the resolution also, it wouldn't change at first from 1024x768.

Here's the greasemonkey script for easy install,

[http://userscripts.org/scripts/show/88189](http://userscripts.org/scripts/show/88189)

Good luck !.

Edited to add:
Another solution is installing a firefox plugin called 'Flashblock', it blocks the crash causing advertisement, before the match.

---

