---
title: "why a kubuntu load screen?"
date: 2006-08-11
forum: Desktop Environments
---

### Post by JohnJSal on 2006-08-11
Last night I installed the KDE desktop to test it out, and I logged off and back in with a KDE session as a one-time thing. My default is still GNOME, and it still boots into GNOME normally, but now during the startup screen when everything is being initialized (with all the "OK"s and the progress bar), it shows the Kubunut symbol/name instead of Ubuntu. Is this normal after installing KDE? Shouldn't it show the name of the default session manager, which is still GNOME/Ubunut?

Thanks.

---

### Post by llamakc on 2006-08-11
I did the same thing and haven't found time to go back to the Ubuntu splash instead of the KUbuntu one.

usplash is the name of the package that takes care of this for us. I'm gonna try and change it back now.

---

### Post by llamakc on 2006-08-11
Edited to remove bad advice. See below.

---

### Post by llamakc on 2006-08-11
Oh duh on me. The splashes are here:

/usr/lib/usplash and there's a symlink pointing to the /etc/alternatives/usplash-artwork.so.

So how do you change it? Easily:

sudo update-alternatives --list usplash-artwork.so

Now, do the same thing but use --config:

sudo update-alternatives --config usplash-artwork.so

```

There are 3 alternatives which provide `usplash-artwork.so'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/lib/usplash/usplash-default.so
*+    2        /usr/lib/usplash/kubuntu-splash.so
      3        /usr/lib/usplash/xubuntu-splash.so

Press enter to keep the default
[*], or type selection number:

```

Choose the one you want. The normal Ubuntu one is number 1.

Reboot and enjoy!

---

### Post by etank on 2006-08-11
Try running```
sudo aptitude remove kubuntu-artwork-usplash
```

---

### Post by JohnJSal on 2006-08-11
> **llamakc said:**
> So how do you change it? Easily:

sudo update-alternatives --list usplash-artwork.so

Now, do the same thing but use --config:

sudo update-alternatives --config usplash-artwork.so

Thanks much. But here's one for you: I did as you said and chose the default, then I reset. During the shutdown phase, the Ubuntu screen was back, so I thought all was normal. But as Ubuntu loaded back up after the reset, it still showed the Kubuntu loadup screen!

Here's the result after checking the alternatives again after resetting. Perhaps the '+' is causing some problem?

```
There are 2 alternatives which provide `usplash-artwork.so'.

  Selection    Alternative
-----------------------------------------------
*     1        /usr/lib/usplash/usplash-default.so
 +    2        /usr/lib/usplash/kubuntu-splash.so

Press enter to keep the default[*], or type selection number:
```

---

### Post by llamakc on 2006-08-11
Nope, same result here. I get the plain Ubuntu shutdown splash but still the Kubuntu startup splash.

However doing a  

sudo dpkg-reconfigure linux-image-`uname -r`

fixed it for me.

---

### Post by user1397 on 2006-08-11
yep this bug is mentioned in my howto, the first link in my sig.  next time, try following that guide and it'll really be easier on you.

---

### Post by llamakc on 2006-08-11
Sweet howto. Thanks.

---

### Post by JohnJSal on 2006-08-12
Thanks!

---

