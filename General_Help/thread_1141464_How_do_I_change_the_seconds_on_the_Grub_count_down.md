---
title: "How do I change the seconds on the Grub count down when choosing an OS?"
date: 2009-04-28
forum: General Help
---

### Post by redonwhite on 2009-04-28
Hello,

I have my computer set up so when I boot up I have the option to either boot Ubuntu 9.04 or Windows XP.  There is a countdown ticker.  Its set at around 10 seconds i think, not positive.  I would like to shrink that down to 3 seconds.  How would i go about doing this?  Thank you for your help!

---

### Post by unutbu on 2009-04-28
For a GUI way, see [http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177).

For a CLI way, open a terminal (Applications>Accessories>Terminal) and type

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
gksu gedit /boot/grub/menu.lst
```

Change

```
timeout 10
```

to 
```

timeout 3
```

---

### Post by ninjapirate89 on 2009-04-28
The above works but if you want a GUI method you can use startupmanager.
```

sudo apt-get install startupmanager

```

---

### Post by redonwhite on 2009-04-28
> **unutbu said:**
> For a GUI way, see [http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177).

For a CLI way, open a terminal (Applications>Accessories>Terminal) and type

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
gksu gedit /boot/grub/menu.lst
```

Change

```
timeout 10
```

to 
```

timeout 3
```

Works like a charm thank you!

---

