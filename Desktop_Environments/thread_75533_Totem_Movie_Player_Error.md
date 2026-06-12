---
title: "Totem Movie Player Error"
date: 2005-10-13
forum: Desktop Environments
---

### Post by ams on 2005-10-13
I just created a WinXP/Ubuntu multiboot system this afternoon. Everything seems to have installed correctly, including the boot loader (WOO!). Anyways, I popped in a DVD to see what would happen. Totem Movie Player opened automatically and gave this error:

[[IMG]http://img109.imageshack.us/img109/7759/screenshot7go.th.png[/IMG]](http://img109.imageshack.us/my.php?image=screenshot7go.png)

Is there anyway to fix this? It is happening with every DVD I try. Thanks.

I am a new linux user :D

---

### Post by dbott67 on 2005-10-13
Have you installed the [DVD Codecs]("http://www.ubuntuguide.org/#dvdplayback") yet?

If not, you need to enable the [extra repositories]("http://www.ubuntuguide.org/#extrarepositories") and type the following command from the terminal:
```
sudo apt-get install libdvdcss2
```

If you haven't already found this little gem, I'd add it to your bookmarks. It is the key to the Ubuntu universe! :)
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

-Dave

---

### Post by Wolki on 2005-10-13
This won't work anymore.

There are solutions however, take a look here: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

Sections 2&3 will set yout ubuntu to a multimedia powerstation, follow the instructions closely to avoid errors. If you get problems (some mirrors might have problems right now, for example), post your errors.

(Make especially sure you remove the line you add in section 3 to your /etc/apt/sources.list again before doing any upgrade or things might break.)

---

