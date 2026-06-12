---
title: "Something strange..."
date: 2009-05-25
forum: Desktop Environments
---

### Post by Cery on 2009-05-25
Okay, this is very odd, I booted up my machine today and to my surprise Ubuntu booted into the terminal...no desktop environment whatsoever. I rebooted, same again. So I did sudo apt-get install ubuntu-desktop, rebooted, and presto, everything back the way it was.

What I'm really confused about is how this happened...I'm pretty damn sure I didn't remove it myself, and the auth log shows me installing it but nothing about it being removed the night before (when everything was fine).

Anyone care to hazard a guess at what happened, or where I should look to investigate?

---

### Post by Sarai the Geek on 2009-05-25
> **Cery said:**
> Okay, this is very odd, I booted up my machine today and to my surprise Ubuntu booted into the terminal...no desktop environment whatsoever. I rebooted, same again. So I did sudo apt-get install ubuntu-desktop, rebooted, and presto, everything back the way it was.

What I'm really confused about is how this happened...I'm pretty damn sure I didn't remove it myself, and the auth log shows me installing it but nothing about it being removed the night before (when everything was fine).

Anyone care to hazard a guess at what happened, or where I should look to investigate?

The ubuntu-desktop package doesn't contain any software, it links to a bunch of other packages. So technically you could uninstall the entire ubuntu-desktop without actually removing that package. Had you removed *anything* the night before? If you accidentally try to remove a package that all the ubuntu-desktop packages depend on, apt-get/synaptic will automatically want to remove all those packages too. 
This happened to me once, I was lucky enough to catch it before it did anything. It does give a warning that lists all the packages it wants to uninstall, but it can be easy to miss if you're not paying attention, especially in synaptic.

---

### Post by Cery on 2009-05-25
I guess I may have done, an error on my part does seem like the most likely explanation...I'll have to read the confirmations more carefully in future... :)

Thanks for your help.

---

### Post by Sarai the Geek on 2009-05-25
> **Cery said:**
> I guess I may have done, an error on my part does seem like the most likely explanation...I'll have to read the confirmations more carefully in future... :)

Thanks for your help.
It's a little harder to miss something like this when you're using apt-get (in the terminal) instead of synaptic because the gui of synaptic contains it all in this little box that is collapsible, whereas apt-get has to list each one out- and there are enough packages in ubuntu-desktop that you should get suspicious before you agree to remove them. Just a thought. ;)

---

