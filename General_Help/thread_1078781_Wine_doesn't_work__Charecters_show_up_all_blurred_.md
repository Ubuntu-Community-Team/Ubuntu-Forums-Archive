---
title: "Wine doesn't work?  Charecters show up all blurred in set up file, games won't play.."
date: 2009-02-23
forum: General Help
---

### Post by tombom62 on 2009-02-23
Here's a screenshot:
[IMG]http://img6.imageshack.us/img6/9498/kq1install.png[/IMG]
What the heck?  I just got xubuntu working, so this had happened from the start.  Also, it doesn't play games with any graphics at all.  I imaging it's a graphical problem, I have a 5200fx graphics card.

ANY HELP?

thanks,
tombom:popcorn:

---

### Post by tombom62 on 2009-02-23
Help?
bump

---

### Post by mb_webguy on 2009-02-23
Are you using the most recent version of Wine from the [WineHQ repository]("http://www.winehq.org/download/deb"), or are you using the version in the Ubuntu repos?

---

### Post by tombom62 on 2009-02-23
it's the latest, I did sudo apt-get after adding the line or whatever

---

### Post by tombom62 on 2009-02-24
bump.  still haven't figured it out, any ideas?  I have the 5200fx card, and I thought it was up to date , but I'm not sure, anyone have any help please?

thanks.

---

### Post by tombom62 on 2009-02-24
> **tombom62 said:**
> bump.  still haven't figured it out, any ideas?  I have the 5200fx card, and I thought it was up to date , but I'm not sure, anyone have any help please?

thanks.
bump


HELP?

---

### Post by tombom62 on 2009-02-24
HHELP!!!!  I really need this!

---

### Post by tombom62 on 2009-02-24
bump.:guitar:
PLEASE?

---

### Post by todak on 2009-02-24
```
sudo apt-get install msttcorefonts
``` If that returns an error, then you need to enable the medibuntu repository as explained [here]("https://help.ubuntu.com/community/Medibuntu"). Or you can look [here]("http://ubuntuforums.org/showthread.php?t=1036323") and see if that helps.

---

### Post by tombom62 on 2009-02-24
thanks, tried all that, but no luck.  would re-installing wine totally help?

---

### Post by todak on 2009-02-24
It might. It won't hurt to try. Remove all of your configuration files, too ```
sudo apt-get remove --purge wine && sudo apt-get install wine
```

---

### Post by tombom62 on 2009-02-27
i fixed it from the advise in the other thread you gave me, thanks!

---

