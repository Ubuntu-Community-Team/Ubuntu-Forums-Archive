---
title: "Firefox? or flash problems."
date: 2009-05-18
forum: General Help
---

### Post by qjmoss on 2009-05-18
I'm going to try to explain why my frustration is rising. 

First I thought I was having problems with Flash, but over the days, I see more problems with my web browsing experience.

First I was just lagging adds, and you tube videos, now firefox is laggy to bring up, and close.

Slow scrolling 


For example, when I hit bookmarks, it lags to open,and so on.

I want to say this is a bug in firefox, but I feel there is a different fix. 

I dont want to back up my book marks either ;)

Maybe just a package I can install, instead of losing my browser.

hm.


I don't know.   But I can't take it any longer, I'm loosing my mind

---

### Post by lovinglinux on 2009-05-18
Have you tried starting Firefox in safe mode?

```
firefox -safe-mode
```

You could also try creating a new profile, just for testing, to see if it is something related to your profile, like a problematic extension or a corrupted database.

```
firefox -P
```

---

### Post by paradigm2 on 2009-05-18
In my opinion, 3.0.x is not even worth it any more.  Even though it isn't an official release yet, I find firefox 3.5 to be FAR superior and I highly recommend it for a intermediate to advanced user...  Memory usage is far superior, as is processor utilisation (which might cause issues such as what you describe, you will see this in system monitor).

[https://launchpad.net/~fta/+ppa-packages](https://launchpad.net/~fta/+ppa-packages)

---

### Post by qjmoss on 2009-05-18
Heres the problem...


Out of my two years using Ubuntu, I've never really asked because I thought it was a stupid question, and I've always tried to avoid it...

But uhm....


How do you add repos. I know you can go into synapatic and add them..

But theres a deb ------ and a deb src- or something whenever I look at them.

And i can never add the public key.


Sorry if this a noob question... I guess we all have our down falls..



But yes, I am using 3.0.10


So maybe I'm ready for an upgrade.. my browsing experience is... terrible

---

### Post by paradigm2 on 2009-05-19
Sure,   This should help you a lot:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Generally you just need to add the regular deb, not the src (source code).

---

### Post by qjmoss on 2009-05-19
How do I get the authentication.


This is all thats here

This repository is signed with  1024R/247510BE OpenPGP key.

---

### Post by lovinglinux on 2009-05-19
> **qjmoss said:**
> How do I get the authentication.


This is all thats here

This repository is signed with  1024R/247510BE OpenPGP key.

Right-click the key link and "save it as" on your desktop, then open "System >> Administration >> Software Sources", then click the "Authentication" tab, thn click the "Import Key File", select the key you saved on your desktop.

---

### Post by qjmoss on 2009-05-19
What i did was click it, and i followed the link that gave me a full key.   or umm...   a lot more code. 

I saved in a text document, and tried to open it, i read that it is the correct way to do this.

And nothing happened =/

---

### Post by Soul-Sing on 2009-05-19
If its een flash non free issue with pulseaudio, you could try gnash( common) and the gnash mozillaplugin. its version 0.8.5, and works fine with youtube and pulseaudio. and its open source....

---

