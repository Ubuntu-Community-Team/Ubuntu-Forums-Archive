---
title: "KDE Does Not Load!!"
date: 2009-07-04
forum: Desktop Environments
---

### Post by izizzle on 2009-07-04
I need major help with this problem. I am running Kubuntu 64-Bit, and here is my problem: The system loads fine and I input my password at the login manager and it continues. Then, when KDE shows the screen with little icons for everything that is loading ([http://www.prashanthellina.com/images/kde4_loading.png](http://www.prashanthellina.com/images/kde4_loading.png)), it freezes at the icon for the internet. I don't think it's a problem with the internet though. 

It gives the following error: "No write access to /home/username/.ICEauthority. KDE is unable to start."

When I click OK, I get this error:
"Could not start ksmserver. Check your installation."

It was working fine and all of a sudden this happened.

Any help is appreciated!!

Thanks.

---

### Post by izizzle on 2009-07-04
I fixed it. For other with the same problem, here is the fix:

Load into a failsafe terminal and log in.

run the following command: ```
sudo chown username:username /home/username/.ICEauthority
```

then run ```
sudo reboot
```

You should be able to log in again.

---

