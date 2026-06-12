---
title: "How to recover from Compiz crash on ubuntu 12.04"
date: 2015-08-16
forum: Desktop Environments
---

### Post by lu333031 on 2015-08-16
After I start up my system (single OS, 32-bit Ubuntu 12.04 only), it is now unable to go beyond taking my login and password and gives the error message "The application Compiz has closed unexpectedly". I tried relaunching and nothing happens. Have tried several times and the same thing happens.

What I did before this started - I chose to apply the available updates for the 12.04 version using the Update Manager. For a long time, it was just spinning and did not seem to be downloading anything. So I canceled the update. It seems that it has left my system in some half-updated state! . The login screen background is different now from before (at least what it displays in its possibly half-baked state).

Is there a way to revert to the old 12.04 level that I had till I attempted to apply the updates?  How can I fix this without reinstalling the system?

I am currently not interested in upgrading to ubuntu 14.x or any other versions.

Thank you.

Lu

---

### Post by ajgreeny on 2015-08-16
At the login screen hit Ctrl+Alt+F1 and then login to the command line with your username and password (password does not show on screen).

Once logged in try to run ```
sudo apt-get update
``` followed by ```
sudo apt-get upgrade
```

If that throws error messages try ```
sudo dpkg --configure -a
sudo apt-get install -f
```

---

### Post by lu333031 on 2015-08-17
Thank you very much. That fixed it.

Lu

---

