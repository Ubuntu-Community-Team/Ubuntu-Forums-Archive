---
title: "new with linux -need help with aircrack"
date: 2009-04-16
forum: General Help
---

### Post by davis6 on 2009-04-16
hi 
i am new with linux 
i want to try running airodump-ng trough terminal but when i type airodump  i get error tha i need to enable component called 'universe'?
what thas it meen?

---

### Post by kpkeerthi on 2009-04-16
Look in System -> Administration -> Software Sources. There you can enable universe and multiverse repositories.

[http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html](http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html)

---

### Post by davis6 on 2009-04-16
thanks- now i get that the program airodump-ng is not install
when i type sudo apt-get instal aircrack-ng it says :"E: couldnt find package aircrack-ng
?

---

### Post by kpkeerthi on 2009-04-16
It seems to exist in the repository:
[http://packages.ubuntu.com/intrepid/aircrack-ng](http://packages.ubuntu.com/intrepid/aircrack-ng)

Try this:
```
sudo apt-get update && sudo apt-get install aircrack-ng
```

---

### Post by davis6 on 2009-04-16
thanks it help-now i tried to write like it says on aircrack :
airmon-ng start rausb0
airodump-ng rausb0 

but i get an error:"This program requires root privileges."
?

---

### Post by kpkeerthi on 2009-04-16
To start the program with root privilege prefix the command with **sudo**
```

sudo airmon-ng start rausb0

```

---

### Post by davis6 on 2009-04-16
i get :
Interface       Chipset         Driver

wlan0           Unknown         Unknown (MONITOR MODE NOT SUPPORTED)

?
i have edimax 7128g wifi pci adepter do i need to pach it>?

---

### Post by kpkeerthi on 2009-04-16
I'm out of options. Sorry friend.

---

