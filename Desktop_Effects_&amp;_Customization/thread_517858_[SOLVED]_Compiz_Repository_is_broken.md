---
title: "[SOLVED] Compiz Repository is broken"
date: 2007-08-05
forum: Desktop Effects &amp; Customization
---

### Post by xIke on 2007-08-05
Trevinos repository doesn't work.

Adding the following lines no longer work (I've done this before no problem).
```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

```
Couldn't find any package whose name or description matched "compizconfig-settings-manager"
Couldn't find any package whose name or description matched "compiz-fusion-plugins-extra"
Couldn't find any package whose name or description matched "compiz-fusion-plugins-unofficial"
Couldn't find any package whose name or description matched "libcompizconfig-backend-gconfsudo"

```

Could someone post a fix for this and possibly sticky it?  I've noticed (unanswered) questions about this buried in large compiz threads.

Thanks,
-xike

---

### Post by hyperair on 2007-08-05
Maybe the repository is down. Try again later.
```

sudo apt-get update
sudo apt-get install compiz-fusion* compizconfig-settings-manager

```

---

### Post by mr-bean on 2007-08-05
Are you running 64bit Ubuntu?
I had to add "-amd64" to the end of mine to get it working.

Not sure if that'll help you

---

### Post by ronmarley1 on 2007-08-05
Seems to be up now.

---

### Post by xIke on 2007-08-05
I am running 64 bit, that's probably it.  Thanks, I'll report back here if that fixes it.

---

### Post by enharrin on 2007-08-05
I am seeing the exact same missing packages, and I am *not* using 64-bit ubuntu.  Has anyone gotten this working?

---

### Post by mr-bean on 2007-08-05
Have you added the security key?

```
sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```

---

### Post by enharrin on 2007-08-05
Yeah, I did that.  Still can't fine those 4 packages.

---

### Post by mr-bean on 2007-08-05
.....and you updated the package list?

```
sudo apt-get update
```


If you did all those things, I can't understand why you're not seeing the packages?

---

### Post by enharrin on 2007-08-05
Gah!  Totally forgot about that.  Well, I had done it, but when I did I had so far forgotten to write the changes to my sources.list, and after I remembered to write them I forgot to update again...  Thanks!  :)

---

