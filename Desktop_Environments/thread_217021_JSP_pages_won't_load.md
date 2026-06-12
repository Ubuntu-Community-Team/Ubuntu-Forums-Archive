---
title: "JSP pages won't load"
date: 2006-07-16
forum: Desktop Environments
---

### Post by moore.bryan on 2006-07-16
running swiftfox on dapper and any .jsp page won't load; everything else is fine.  downloaded, installed, and verified latest JRE from sun.  other java applets load.  any ideas?

---

### Post by bluecherry on 2006-07-16
Did you notice this beheavior on more then one site?

I'm asking because .jsp stands for Java Server Pages, meaning the server handles the java part and sends the output (HTML or other) to the browser.
So you do not need Java on your pc to browse jsp-driven sites..

---

### Post by moore.bryan on 2006-07-16
bluecherry: thanks for the quick reply...

i noticed it on more than one page; both the pennsylvania department of motor vehicle driver licensing center page and reserveamerica.com login page don't work in ubuntu, but fine with firefox in windows.  

?

---

### Post by ardchoille on 2006-07-16
> **moore.bryan said:**
> bluecherry: thanks for the quick reply...

i noticed it on more than one page; both the pennsylvania department of motor vehicle driver licensing center page and reserveamerica.com login page don't work in ubuntu, but fine with firefox in windows.  

?

I have reserveamerica.com working fine in my firefox (on Ubuntu 6.06) and I have no plugins at all.

---

### Post by bluecherry on 2006-07-16
np!

I visited reserveamerica.com and went to the login page and it showed up fine.

Couldn't find the other site...

Check these for me:
1. Are you running the latest firefox? I've got 1.5.0.4 (go to Help > About Mozilla Firefox), running Dapper.

2. Have you got any firefox plugins or extensions installed (name + version)

3. Check if JSP is listed in: Edit > Preferences > Downloads (tab) > Actions .... (button on bottom of tab). If it is delete it. 
This is a long shot and I don't see why it would be listed here, but you never know. :)

---

### Post by bluecherry on 2006-07-16
I forgot: try control + shift + reload to be sure firefox is not using some corrupted cached version of this page.

---

### Post by moore.bryan on 2006-07-16
> **bluecherry said:**
> np!

I visited reserveamerica.com and went to the login page and it showed up fine.

Couldn't find the other site...

Check these for me:
1. Are you running the latest firefox? I've got 1.5.0.4 (go to Help > About Mozilla Firefox), running Dapper.

2. Have you got any firefox plugins or extensions installed (name + version)

3. Check if JSP is listed in: Edit > Preferences > Downloads (tab) > Actions .... (button on bottom of tab). If it is delete it. 
This is a long shot and I don't see why it would be listed here, but you never know. :)

1.  i've got 1.5.0.4
2.  i uninstalled all extensions and no luck
3.  it's not there.

it's so inconvenient, so i really appreciate your help.

---

### Post by bluecherry on 2006-07-17
Sorry moore.bryan, i've looked around on the internet for similar bugs but couldn't find anything...

Maybe somebody else has got a more extended knowledge of firefox and advanced settings?

---

### Post by moore.bryan on 2006-07-17
thanks for your attempts anyway!  i think it has something to do with .jsp pages on secure servers.  i was on a site which had the choice of both; the secure page would not load, the unsecure did.  who knows... 

thanks, again...

---

