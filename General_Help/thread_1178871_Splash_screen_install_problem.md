---
title: "Splash screen install problem"
date: 2009-06-05
forum: General Help
---

### Post by tml240 on 2009-06-05
I've looked at multiple threads to get splash screen themes to work.

I'm trying to use [Usplash Fingerprint Theme]("http://www.gnome-look.org/content/show.php/Asufi+High+Tech+Usplash+Theme?content=98360").

I tried the following

1) Install startup manager, add the splash add-on, update
2) Install via command line
```
sudo cp usplash-theme-fingerprint.so /usr/lib/usplash
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-fingerprint.so 10
sudo update-alternatives --config usplash-artwork.so

```
3) Also update the menu.lst (added vga=791)

Yet I only get the verbose version of boot-up with high resolution.

Is there something I'm missing?

Thanks

---

### Post by talava on 2009-06-05
***[I Failed to properly read your post before answering. Sorry!]***

Try installing package 'Startup-manager' in synaptic. Then choose your desired splash there, if it's listed.

---

