---
title: "adobe flash and google chrome"
date: 2012-09-30
forum: Desktop Environments
---

### Post by bblackbelt on 2012-09-30
Hello guys, how can I install adobe flash (or something equivalent) and chrome on Lubuntu 12.04 ppc?  I have found nothing with apt-cache.

thanks in advance

---

### Post by akoskm on 2012-09-30
Install Chrome from [https://www.google.com/intl/en/chrome/browser/]("https://www.google.com/intl/en/chrome/browser/")
[Adobe Flash Plugin in Lubuntu]("http://ubuntuforums.org/showthread.php?t=1493672")

---

### Post by kc1di on 2012-09-30
> **bblackbelt said:**
> Hello guys, how can I install adobe flash (or something equivalent) and chrome on Lubuntu 12.04 ppc?  I have found nothing with apt-cache.

thanks in advance

The best way I find to do this is in a terminal install the following:

```
sudo apt-get install lubuntu-restricted-extras lubuntu-restricted-addons
```

This will install flash plugin along with all the other codecs you'll need to play dvd's mp3 etc.
in fact you can find the details on this page:
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")
good luck.

---

### Post by bblackbelt on 2012-09-30
> **kc1di said:**
> The best way I find to do this is in a terminal install the following:

```
sudo apt-get install lubuntu-restricted-extras lubuntu-restricted-addons
```This will install flash plugin along with all the other codecs you'll need to play dvd's mp3 etc.
in fact you can find the details on this page:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
good luck.


I already run those commands and all the software have bee installed  without errors. still I have no video in youtube. what's wrong? 
thanks

---

### Post by bblackbelt on 2012-09-30
> **akoskm said:**
> Install Chrome from [https://www.google.com/intl/en/chrome/browser/](https://www.google.com/intl/en/chrome/browser/)
[Adobe Flash Plugin in Lubuntu]("http://ubuntuforums.org/showthread.php?t=1493672")


thanks for the link, but seems that chrome is not available for powerpc

---

### Post by kc1di on 2012-09-30
> **bblackbelt said:**
> thanks for the link, but seems that chrome is not available for powerpc

why not install chromium-browser from the repository it works for me.
```
sudo apt-get install chromium-browser
```

It's the open source chrome and is basically the same.

---

### Post by bblackbelt on 2012-09-30
> **kc1di said:**
> why not install chromium-browser from the repository it works for me.
```
sudo apt-get install chromium-browser
```It's the open source chrome and is basically the same.


does it need a different entry in the source.list file? apt is unable to locate it!

---

### Post by zombifier25 on 2012-09-30
> **bblackbelt said:**
> does it need a different entry in the source.list file? apt is unable to locate it!

Try updating your program database:
```
sudo apt-get update
```
And no, chromium comes in Ubuntu's repo, so no need for external PPA.

---

