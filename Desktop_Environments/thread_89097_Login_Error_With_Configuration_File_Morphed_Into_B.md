---
title: "Login Error With Configuration File Morphed Into Bigger Issue"
date: 2005-11-11
forum: Desktop Environments
---

### Post by faceoftheearth on 2005-11-11
When I start up Ubuntu I get an error message about the configuration file. I went to Ubuntu Forums and found that the following fixed that problem.
```

sudo /etc/init.d/gdm stop
sudo apt-get remove gdm --purge
sudo apt-get install gdm ubuntu-desktop
sudo /etc/init.d/gdm start

```
When I attempted to do this I discovered a larger problem. The Gnome GUI stops, which it is supposed to, however it just goes to the screen that you get at the start which lists things like "calculating module dependencies" and what not followed by [OK.] I can't go anywhere from there, no buttons do anything. The only response I can get is by hitting the power button, which gives the message "Sending all processes the term signal" and then goes to a pure black screen with the cursor at the top left blinking. From there no buttons have any effects. What should I do?

---

