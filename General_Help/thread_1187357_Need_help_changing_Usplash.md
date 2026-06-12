---
title: "Need help changing Usplash"
date: 2009-06-14
forum: General Help
---

### Post by ~sHyLoCk~ on 2009-06-14
Hi! I tried to change my usplash [bootscreen] using startup-manager,but it just shows a black screen running verbose mode while booting! I lso tried to install these: [Url1]("http://www.gnome-look.org/content/show.php/Sleek+Dragon+for+Usplash?content=51556")and [Url2]("http://www.gnome-look.org/content/show.php/Afisufi+High+Tech+Usplash+Theme?content=98360") .so files manually using:

```
"sudo mkdir -p /usr/local/lib/usplash/"

"sudo cp Sleek_Dragon_Usplash_Splash-02.so /usr/local/lib/usplash/Sleek_Dragon_Usplash_Splash-02.so"

"sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/local/lib/usplash/Sleek_Dragon_Usplash_Splash-02.so" 55"

"sudo update-alternatives --config usplash-artwork.so"

"sudo dpkg-reconfigure linux-image-$(uname -r)"
```

However I still can't see any usplash screen! Please help!

EDIT: I forgot to mention I use Jaunty, although I think that would have made a little difference.

---

### Post by Soul-Sing on 2009-06-14
basic wiki: [https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash)
with a xubuntu example......
I think you have to update initramfs

---

### Post by ~sHyLoCk~ on 2009-06-14
> **leoquant said:**
> basic wiki: [https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash)
with a xubuntu example......
I think you have to update initramfs

Ok I did that but still the same! Is it because I had edited my grub and maybe that's why it's not working? I just renamed the "titles" and changed the timeout to 5sec.

---

### Post by theozzlives on 2009-06-14
I think their gonna do away with usplash as we know it, that's why the custom ones don't work.

---

### Post by QIII on 2009-06-14
Did you check to see that the usplash theme had been tested on Jaunty?

It looks like you got the splashes installed in the right place. 

I've encountered splashes that just don't work on Jaunty for some reason, and as a result the fallback is the verbose startup.

---

### Post by QIII on 2009-06-14
TheOzzLives is correct about usplash.

It won't be supported any longer in Karmic ...

---

### Post by ~sHyLoCk~ on 2009-06-14
> **QIII said:**
> TheOzzLives is correct about usplash.

It won't be supported any longer in Karmic ...
What if I follow [this]("http://maketecheasier.com/create-install-your-own-usplash-theme-in-ubuntu/2009/01/25")? Will it work or screw up my system?

---

### Post by ~sHyLoCk~ on 2009-06-14
Ok forget it I can't install splashy, it's showing: 

```
E: /var/cache/apt/archives/splashy_0.3.13-3ubuntu1_i386.deb: trying to overwrite `/etc/lsb-base-logging.sh', which is also in package lsb-base

```

---

