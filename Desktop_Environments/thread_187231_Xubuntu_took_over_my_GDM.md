---
title: "Xubuntu took over my GDM"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Yi Ding on 2006-06-02
I installed xubuntu-desktop and it took over my GDM login theme and my init theme.  Is there any way I can get them back to the original ubuntu themes?

---

### Post by hostilepenguin on 2006-06-02
applications -> system-> GDM setup

you'll be prompted for your password then you should see a window that will let you control your GDM. Enjoy!

---

### Post by Yi Ding on 2006-06-02
Great!  It's actually at System->Administration->Login Window on my machine.  However, the background it displays before loading my background is still a light blue, which I think is left over from the Xubuntu theme.

I also found out how to revert the boot and shutdown screens to Ubuntu default
```
sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure linux-image-$(uname -r)
```

---

### Post by Ramses de Norre on 2006-06-02
I've got the light blue screen too and never had xubuntu installed so I think it's default.. (I'm using fluxbox with gdm).

---

### Post by Yi Ding on 2006-06-02
OK, if that's true, that fixes my problem then.  Thank you hostilepenguin and Ramses!

---

