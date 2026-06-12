---
title: "Update error message!"
date: 2009-05-25
forum: General Help
---

### Post by Rytron on 2009-05-25
Hi.
Whenever I do an update I get this update error message (attached picture).
It is not a big deal as I can still update as normal. Its more of an oddity.
Does anyone know how to stop this error message?
Thanks.

---

### Post by taurus on 2009-05-25
Everytime you add a repos to your /etc/apt/sources.list, you also need to import a key for that repo.

[https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA](https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA)

---

### Post by mhh91 on 2009-05-25
yes,the packages you are trying to install are not signed :)

---

### Post by Rytron on 2009-05-26
I commented out these two line and now the message does not appear.

```
#deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
#deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
```

I try to import the key but it doesnt pick it up. I presume as I have commented out the above lines, that I wont be able to get the latest Chromium updates? I find it strange that I was still able to update my Chromium browser even though it was not signed.

---

### Post by Rytron on 2009-05-31
I imported the key from [here]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x5A9BF3BB4E5E17B5").

Not sure why it wouldn't import the key before. Perhaps it was the way I saved the text file? No error messages now.

:popcorn:

---

