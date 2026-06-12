---
title: "Problems with Canon BJC 1000 Printer"
date: 2006-09-02
forum: Desktop Environments
---

### Post by BrunoProg64 on 2006-09-02
I have a big problem. I bought two years ago a Canon BJC 1000 Printer and use it perfectly under Windows XP. But recently I switched to Linux, specifically to Ubuntu and I do all and I didn't make it works. What happens?? Some one could help me? I go also to the Canon Web Page in order to search for non-free drivers, but I found nothing. I have Ubuntu 6.06 with GNOME Desktop. On [www.linuxprinting.org](www.linuxprinting.org) it saids that my printer work mostly, but it's supported anyway. Any ideas?? I expect an answer soon.

(Sorry is my english is a little bit bad. I'm learning)

Thanks to all.

---

### Post by whizbaby on 2006-09-02
Try (what I think is the easiest) adding it with the cups-web-frontend:

sudo adduser cupsys shadow   (to enable cups verifying passwords)

then in browser (e.g. firefox)

localhost:631

go to the 'administration' tab and add the printer.
(note: works best with the proper *.ppd file. If cups doesn't have it, download it, usually from manufacturer)


Or munch your way through 

[http://www.linuxprinting.org/kpfeifle/LinuxKongress2002/Tutorial/VII.cups-help/VII.cups-help.html](http://www.linuxprinting.org/kpfeifle/LinuxKongress2002/Tutorial/VII.cups-help/VII.cups-help.html)

---

