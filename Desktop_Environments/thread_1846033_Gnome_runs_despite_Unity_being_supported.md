---
title: "Gnome runs despite Unity being supported"
date: 2011-09-18
forum: Desktop Environments
---

### Post by jakepc123 on 2011-09-18
For some reason on my laptop when I first boot up it automatically uses Gnome rather than Unity. I do however know that my laptop supports Unity because if I log out and then log back in it correctly loads Unity and works perfectly. 

I don't understand why it would be doing this so any help would be great thanks.

---

### Post by Krytarik on 2011-09-18
Try forcing it to load Unity:

[http://www.tuxgarage.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html](http://www.tuxgarage.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html)

Hope it works!

---

### Post by jakepc123 on 2011-09-18
No, that didn't help the problem it still seems to be booting into Gnome. :-(

---

### Post by Krytarik on 2011-09-18
Please post the output of:
```
ls -al /var/cache/gdm/USERNAME/dmrc
```

---

### Post by jakepc123 on 2011-09-18
```
-rw-r--r-- 1 jake jake 73 2011-09-18 14:00 /var/cache/gdm/jake/dmrc

```


> **Krytarik said:**
> Please post the output of:
```
ls -al /var/cache/gdm/USERNAME/dmrc
```

---

### Post by Krytarik on 2011-09-18
> **jakepc123 said:**
> ```
-rw-r--r-- 1 jake jake 73 2011-09-18 14:00 /var/cache/gdm/jake/dmrc

```
The permissions are fine here, so not many more things that come into question:

- Check this file and the file ".dmrc" in your home directory for differences, they should be the same, and the entry for "Session" should be "gnome".

- Make sure the default session in the "Login Screen" settings is set to "Ubuntu", though I don't think that this still has any effect on your user.

---

### Post by jakepc123 on 2011-09-19
No that all seems fine.
I may just have to live with it until 11.10 and see if that sorts it.

Thanks anyway for all your help.

---

### Post by fjgaude on 2011-09-19
> **jakepc123 said:**
> For some reason on my laptop when I first boot up it automatically uses Gnome rather than Unity. I do however know that my laptop supports Unity because if I log out and then log back in it correctly loads Unity and works perfectly. 

I don't understand why it would be doing this so any help would be great thanks.

When you log out is there not an option to select the GUI you are to use?

I'll have to see what it is by going back to 11.04. I'll let you know what I find.

**LATER**: When I log out at the bottom of the display after clicking on who is to log in are options. I can chose gnome, unity, and others. What you are saying that your selection of unity doesn't stick on reboot?

---

### Post by Blasphemist on 2011-09-19
It sounds to me like auto login is being used and that the default session is not set to Ubuntu. Go to system settings, login screen and change the default session to Ubuntu. You can also turn off auto login but that isn't necessary.

---

### Post by jakepc123 on 2011-09-21
**fjgaude**
Thats what I thought but it says "Ubuntu" (not ubuntu classic) even just before it boots into Gnome.

**Blasphemist**
I have gone and checked and again there it says "Ubuntu"

---

