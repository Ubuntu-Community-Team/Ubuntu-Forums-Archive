---
title: "How can I get information about my computer?"
date: 2008-12-26
forum: General Help
---

### Post by fbjoey on 2008-12-26
Could anyone tell me how to get information about my computers. 
Just stuff like what sounds card I have, how much ram, all the stuff that you cant see without opening my computer.

I just want to build a list with this information so I can reference to it when I have problems with my computer.

Thank you.

---

### Post by jerome1232 on 2008-12-26
```
sudo lshw
```

Your going to get alot of  stuff from that command so you can make it a nice html page instead

```
sudo lshw -html >system.html
firefox system.html
```


also these commands list pci devices and usb devices respectivly.
```
lspci
lsusb
```

---

### Post by fbjoey on 2008-12-26
Cheers mate :D

---

