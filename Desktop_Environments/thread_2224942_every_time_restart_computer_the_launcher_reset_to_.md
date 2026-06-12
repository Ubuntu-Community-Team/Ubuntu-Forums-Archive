---
title: "every time restart computer the launcher reset to default."
date: 2014-05-19
forum: Desktop Environments
---

### Post by 13718484207 on 2014-05-19
Recently, I reinstall the ubuntu, and remain the home dir. 
Now when i restart my computer, the launcher setting gone, for example, i lock chrome web brower to the launcher, but when i restart my computer it return to the default setting, 
the chrome is gone from the launcher, but i also can start chrome from terminal.

has anyone know the question? think you.

---

### Post by tfrue on 2014-05-19
This may not be what you want to hear, nor is it necessarily an answer, but I had a similar issue just last week. I had to shut down my computer due to it freezing, and when I rebooted, it had set all the defaults of everything and I was unable to change them even as root. So after playing with it for hours, I decided to back up my files and start over with a fresh install of Ubuntu. Saved time and a massive headache and now it works great! LOL!

---

### Post by 13718484207 on 2014-05-19
I have configured my computer and installed some software, but I don't do that again.:( :(

---

### Post by Frogs Hair on 2014-05-19
You can try Unity reset after installing the dconf editor.```
sudo apt-get install dconf-tools
``````
setsid unity

``` Note: the guest account/session doesn't save any settings after the session is closed in-case you or anyone else uses that account.

---

