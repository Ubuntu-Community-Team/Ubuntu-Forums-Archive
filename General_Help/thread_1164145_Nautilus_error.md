---
title: "Nautilus error"
date: 2009-05-19
forum: General Help
---

### Post by brunogermain on 2009-05-19
Hi there,
i'm almost an ubuntu newbie.
i recently tried to compile glib-2.19 on ubuntu jaunty. the installation was successful, but after that nautilus won't open the "computer" location.
the error message says "Could not display "Computer". same with the trash.
also, unless i force mount them, ubuntu won't auto mount my internal IDE hd, nor my external USB hd.
if I force mount them from terminal, they're both there and perfectly working

I already tried to autoremove and install nautilus and ubuntu-desktop. installations were both successfull, but nothing changed.

Any suggestions?

Thanks!

---

### Post by pro003 on 2009-05-19
install ntfs-config, thats the simple way of mounting drives 

in terminal
```

sudo aptitude update
sudo aptitude install ntfs-3g && sudo aptitude install ntfs-config
```

now go to Applications > System Tools and start Ntfs-Config, the rest of it its easy...

you should be able to read/write on any drive that you have enabled...

---

### Post by brunogermain on 2009-05-19
thanks for the suggestion!
it worked for the IDE drive, but not for the USB and nautilus is still misbehaving.
BTW, i just noticed that the toolbar language has changed without touching any settings...

---

### Post by pro003 on 2009-05-20
maybe you have pressed alt+shift, without knowing it it's a shortcut for changing the language...  and to change a language in a toolbar all you need to do is click once on it and maybe you accidentally did it.

---

### Post by brunogermain on 2009-05-20
the language thing is no big deal... but i didn't accidentally hit any key. the language support is set to italian, but all the menus switched to english yesterday. that's it.
my major problem is the nautilus thing. it won't open the computer, network and trash locations anymore. plus my usb drive does not automount.

---

### Post by pro003 on 2009-05-20
as far as network is concerned nautilus could never and it would never open you a network, because its set by default, you can browse network only as user... and for trash I could not empty some of my trash once but I did it successfully through nautilus..
 how do you open nautilus?

 it should be **"gksu nautilus" **

---

### Post by brunogermain on 2009-05-22
no way! also cd/dvd creator is gone. the message says: could not disply "burn:///".
things i tried so far:
- apt-get purge and autoremove nautilus, gnome and ubuntu-desktop.
after reinstalling, nothing changed. 
help!

---

