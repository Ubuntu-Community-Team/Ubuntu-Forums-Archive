---
title: "No Boot Splash"
date: 2005-11-20
forum: Desktop Environments
---

### Post by Beastboy26 on 2005-11-20
SO...
     I have a IBM T43 with ATI 64MB x3000 graphics card.
I have a no splash sreen at boot up.  (running breezy). :confused:
I have looked at the /boot/grub/menu.lst.  I really don't see anything out of place.  I can post it if needed

---

### Post by Ampersand on 2005-11-20
Have you got usplash installed? Check in Synaptic, or run
```
sudo apt-get install usplash
```

I think it's meant to be installed by default, but it's possible that it wasn't.

---

### Post by Beastboy26 on 2005-11-20
Yeah, usplash is installed, I re-installed it just in case, and it still didn't work:???:

---

### Post by ecobuntu on 2005-11-20
Does it say on the kernel line in your /boot/grub/menu.lst file splash?
If not add splash to it

---

### Post by Beastboy26 on 2005-11-21
it is there;

title           Ubuntu, kernel 2.6.12-9-686
root            (hd0,6)
kernel          /vmlinuz-2.6.12-9-686 root=/dev/sda9 ro quiet splash
initrd          /initrd.img-2.6.12-9-686

---

### Post by rejser on 2005-11-21
be happy that you have a faster boot-time :)

---

### Post by Beastboy26 on 2005-11-21
[QUOTE=rejser]be happy that you have a faster boot-time :)[/QUOTE]

hmm... not really, it takes three keystrokes for me to boot ("enter", "ctrl -C" twice) , and I have to boot 3-4 times a day.

hibernate, and suspend also doesn't work :(

---

### Post by ranf on 2005-11-21
[QUOTE=Beastboy26]hmm... not really, it takes three keystrokes for me to boot ("enter", "ctrl -C" twice) , and I have to boot 3-4 times a day.
[/QUOTE]
Ctrl+C to kill what? If you don't want the things you kill, it is better to remove them.

---

### Post by teaker1s on 2005-11-21
check login manager as bootsplash can be disabled

---

### Post by Beastboy26 on 2005-11-21
[QUOTE=teaker1s]check login manager as bootsplash can be disabled[/QUOTE]

how do I go about this? and how would I tell if it is disabled?

---

### Post by Beastboy26 on 2005-11-22
No replies?  Someone has to know! :razz:

---

