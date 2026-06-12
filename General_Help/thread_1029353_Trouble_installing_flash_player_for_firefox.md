---
title: "Trouble installing flash player for firefox"
date: 2009-01-03
forum: General Help
---

### Post by miocene on 2009-01-03
I've been trying to install flash player on Firefox 3. Youtube directs me to the Adobe site where I select the flash package to download. I choose .deb (for ubuntu) and it opens in gdebi installer and appears to install correctly.

But after I still cannot view flash content and am directed back to the Adobe site.

I have restarted the browser and my system several times to no avail.

When I go to about:plugins in FF the flash plugin is not listed.

---

### Post by 2hot6ft2 on 2009-01-03
Did you restart firefox?

Or for the flash and other mulimedia in the repos do the following.

You need to put this in a terminal and hit Enter
Then your password and Enter (your password will not be displayed)
Applications>Accessories>Terminal

```
sudo apt-get install ubuntu-restricted-extras

```
It will fix that as well as other multimedia problems you haven't found out about yet.

When it gets to the agreement hit Tab then Enter to accept the Java agreement.

---

### Post by miocene on 2009-01-03
Got it working, thanks

---

