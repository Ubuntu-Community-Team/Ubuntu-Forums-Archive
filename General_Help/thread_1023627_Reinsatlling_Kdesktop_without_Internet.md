---
title: "Reinsatlling Kdesktop without Internet"
date: 2008-12-28
forum: General Help
---

### Post by cybeh on 2008-12-28
Hi,

By mistake I killed my very well running Kubuntu system fro 2 years. Was experimenting XBMC and removed python-minimal. Didn't knew the bugger will remove all the application associated with it. As a result KDE is gone and am without the desktop manager.

Another problem is I don't have Internet connection as if now and it will be long till I have it my Wireless N adapter is not supported as if now. 

Please help me in reinstalling the desktop environment from a console without internet from the Hardy CD Rom. It would have been great if they had something rescue cd for hardy as well.

Any help will be greatly appreciated.

Cheers,
Cybeh

---

### Post by .nedberg on 2008-12-28
Insert the CD in the drive and in a console do:

```

sudo apt-cdrom add
sudo apt-get install kubuntu-desktop

```
But it might not work if the version on the CD is too old and you have done some updates. It won't hurt though!

---

### Post by cybeh on 2008-12-28
I tried that, but it still connects to the internet and says missing packages. I tried --no-download option as well, along with --fix-missing. No luck, lot of customization went into this install and I have been using this for last 2 years. Its so bad.

To hell with XDMC. Please let me know if you have anymore suggestions.

Cheers,
Cybeh

---

### Post by editrix on 2008-12-29
I'm pretty sure .nedberg's solution will work **provided** you're using the alternate CD. You probably have the live CD version.

---

