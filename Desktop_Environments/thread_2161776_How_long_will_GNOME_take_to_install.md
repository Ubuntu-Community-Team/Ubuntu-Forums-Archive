---
title: "How long will GNOME take to install?"
date: 2013-07-11
forum: Desktop Environments
---

### Post by caraj on 2013-07-11
I used the command sudo apt-get instal gnome-session-fallback, and now the terminal is filling with a bunch of stuff. It's been like ten minutes, and I'd just like to know if I have much time ahead.
Actually, now it says "Idconfig deferred processing now taking place", then "Processing triggers for menu..." and underneath that "username@computer-name:~" but no additional text is appearing. Now what do I do???
Could I, by the way, have put in the wrong command for installing GNOME? I don't know much about command line, so something could've gotten by me probably without much difficulty.
And how do I remove everything this command may have installed, if it comes to that? Would I need to enter another command in the terminal, or is there another way?

---

### Post by mc4man on 2013-07-12
> **caraj said:**
>  now it says "Idconfig deferred processing now taking place", then "Processing triggers for menu..." and underneath that "username@computer-name:~" but no additional text is appearing. Now what do I do???

And how do I remove everything this command may have installed, if it comes to that? Would I need to enter another command in the terminal, or is there another way?
You're done installing, log out & pick one of the gnome sessions at the log in, (greeter) screen


Assuming you're not using 13.10 (saucy), To remove from cli
```
sudo apt-get purge gnome-session-fallback
```

---

### Post by ana551 on 2013-07-12
i think mc4man is right....once the username process is triggered you are done installing.

---

### Post by buzzingrobot on 2013-07-12
When the prompt -- the bit that ends with a "$" -- returns, you're done.  The messages you saw are the normal status messages you should see when an install is moving along properly.  

How long it takes to install software depends on your bandwidth and the size of the downloads.  Gnome is a large and complex system, with many individual files that need to be acquired and installed, so 10 minutes wouldn't be at all unusual.

---

