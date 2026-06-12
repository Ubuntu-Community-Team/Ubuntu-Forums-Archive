---
title: "Panels are missing."
date: 2009-06-20
forum: General Help
---

### Post by wizzim on 2009-06-20
Loading error. How can i fix it?
When I load ubuntu it just goes to the default background and nothing else shows up. The panels are missing. I know this is the result of trying to fix a "644 permissions with .dmrc" I can happily report i fixed the issue with the .dmrc, but as I stated before nothing shows up when i start up ubuntu. I also know how to get into console and xterm, which was used for these codes.

Things I have tried...
```

gconftool-2 --recursive-unset /apps/panel
...
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm restart or sudo /etc/init.d/gdm start


```
What do i do from here?
Thanks!
Wizzim

---

### Post by synapsys on 2009-06-20
Sounds like you screwed up permissions for the home directory.... follow this guide here.

[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

Boot up a livecd if you need to.

---

### Post by mhgsys on 2009-06-20
Looks likes walking in circles here buddy;

[http://ubuntuforums.org/showthread.php?t=1186458](http://ubuntuforums.org/showthread.php?t=1186458)

---

### Post by synapsys on 2009-06-20
Boot to livecd..... mount your /home partition..... follow guide on the link i gave you..... problem solved...... i had the exact same identical problem..... this is how i fixed it.....

---

### Post by wizzim on 2009-07-02
I looked at that link and it says you cant do it from a liveCD and i tried it, not working.

---

### Post by wizzim on 2009-07-02
Is there a way i could back up stuff from it so when i reinstall its all good?

---

### Post by wizzim on 2009-07-03
any help please?

---

### Post by philinux on 2009-07-03
Maygbe this might save you reinstalling. 

[http://forum.pinoygeek.org/index.php/topic,443.0.html](http://forum.pinoygeek.org/index.php/topic,443.0.html)

If not that then there are more suggestions.
[http://www.google.co.uk/search?q=ubuntu+reset+gnome+to+default&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.co.uk/search?q=ubuntu+reset+gnome+to+default&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by wizzim on 2009-07-03
That didn't work either.

---

### Post by wizzim on 2009-07-03
I would like to report that it has worked! thanks so much! :DD:D:

---

### Post by philinux on 2009-07-03
You probably had to log out and back in I guess. Good job.

---

