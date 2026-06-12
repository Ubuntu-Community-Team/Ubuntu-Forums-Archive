---
title: "Strangest problem yet - Thunderbird loves University of Arizona?  Help!"
date: 2006-02-15
forum: Desktop Environments
---

### Post by stynx9000 on 2006-02-15
Hey Folks,

I've been using Ubuntu for about 6 months now as my primary os on my laptop.  So far I haven't found a problem that I can't fix by tinkering, fiddling, forum searching and googling.  Until now.

If anyone sends me a link through an email (which I read using Thunderbird), and I click on that link, I get directed to here:  [http://www.arizona.edu/](http://www.arizona.edu/)

It doesn't matter where the link is, as long as it begins with www. or http: I get sent to the University of Arizona.  If I cut and past the link into any browser, it comes up correctly.

I've had this problem for about a month now, and the strange thing is, I don't think anything's changed with Firefox or Thunderbird.  I grepped through my entire home dir looking for various forms of Arizona and the url, but have come up with nothing but a few things in cache.

Emptying the cache and deleting all of my cookies, history, etc doesn't seem to do the trick.

Any suggestions?

Thanks,
Ben "Go UoA!"

---

### Post by carlosqueso on 2006-02-15
It has to do with the command line argument that you use to launch internet links.  I'm afraid I don't know where that lives (maybe in tbird options), but you have firefox %u in there.  That sends firefox to where you go if you just type a u in the address bar (try it, and the other letters too).   You need to remove the %u and it'll work fine.

---

### Post by John Jason Jordan on 2006-02-15
[QUOTE=stynx9000]If anyone sends me a link through an email (which I read using Thunderbird), and I click on that link, I get directed to here:  [http://www.arizona.edu/](http://www.arizona.edu/)

It doesn't matter where the link is, as long as it begins with www. or http: I get sent to the University of Arizona.  If I cut and past the link into any browser, it comes up correctly[/QUOTE]
I had the same thing happen. Except it wasn't from Thunderbird, it was from Sylpheed, which is what I use for e-mail. Just like you, if I copied and pasted the link into a new tab it worked fine. 

I never figured out what was wrong, but eventually one day it cleared up.

---

### Post by linkunderscore on 2006-02-15
Its a firefox "bug" if you will. You have a %u in there. 

open up firefox and type 'u' in the address bar and press enter


university of arizona pops up. :)

---

### Post by stynx9000 on 2006-02-17
You are all correct, typing u in the address bar does indeed make the U of A website pop up.

So how do I get rid of this? :)

Ben

---

### Post by dcstar on 2006-02-17
[QUOTE=stynx9000]You are all correct, typing u in the address bar does indeed make the U of A website pop up.

So how do I get rid of this? :)

Ben[/QUOTE]
Try System-Preferences-Preferred Applications.

My custom Default Web Browser is set to:

/usr/local/firefox/firefox "%s"

(Because my FF 1.5 is installed in that directory, substitute you own path)

---

### Post by John Jason Jordan on 2006-02-17
[QUOTE=dcstar]Try System-Preferences-Preferred Applications.

My custom Default Web Browser is set to:

/usr/local/firefox/firefox "%s"[/QUOTE]
OK, did that. Previously I had set my home page to a blank page. Now, instead of a blank page, Firefox opens with "Welcome to McDonalds."

Changed it back ot %u. I'd rather put up with the University of Arizona. :)

Who decided to put these bugs in Firefox?

---

### Post by dcstar on 2006-02-17
[QUOTE=John Jason Jordan]OK, did that. Previously I had set my home page to a blank page. Now, instead of a blank page, Firefox opens with "Welcome to McDonalds."

Changed it back ot %u. I'd rather put up with the University of Arizona. :)

Who decided to put these bugs in Firefox?[/QUOTE]
Just remove the "%" stuff, it is supposed to pass a variable onto the application to open it, but if it is not working correctly on your system it is probably due to another issue, not Firefox.

---

