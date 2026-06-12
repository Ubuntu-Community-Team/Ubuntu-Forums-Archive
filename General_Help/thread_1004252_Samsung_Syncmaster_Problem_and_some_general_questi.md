---
title: "Samsung Syncmaster Problem and some general questions"
date: 2008-12-07
forum: General Help
---

### Post by enarsee on 2008-12-07
System Configuration

AMD 64 X2 2.14 Ghz Dual Core
1 gb RAM
Asus M2N MX motherboard
nvidia chipset
Nvidia 6150 SE Geforce in built
REALTEk Audio card
Realtek LAN Card
Samsung Syncmaster 152s

Well i am totally new to linux recieved my ubuntu dvd yesterday and installed it through windows.
After installing when i reboot, after the ubuntu bootscreen goes, the monitor[ Samsung Syncmaster 152s ] goes blank and keeps on switching between standby and on. I connected my old CRT monitor, on which Ubuntu worked. But i did not have the linux driver for the samsung monitor. Then i thought maybe the nvdia graphic card drivers are not present.Therefore i downloaded the  linux drivers from the nvidia website [.run file]When i opened it in ubuntu nothing happened, it suggested that it will download the driver in the Hardware Driver Section. But the internet connection wasnt on in ubuntu. Any Suggestions?

I have a Realtech lan card, and its linux drivers too [.tgz format] How do i install it?

I downloaded wine[wine_1.1.10~winehq0~ubuntu~8.10-0ubuntu1_i386.deb] and opened it in ubuntu, it said that lib2audio or libaudio2 was not there so i couldnt install. ????
One more query, Can we run .exe files on ubuntu? If yes how?

---

### Post by enarsee on 2008-12-09
Bump

---

### Post by rudihawk on 2008-12-09
With that .run file, go to it, right click on it. In one of the tabs there should be an option for you to: "run this file as an executable". Tick that box, and try again to install it.

---

### Post by enarsee on 2008-12-09
@^
in the right click menu there is no such thing as run as excecutable. if I double click on it, it opens gedit and says that cant be decoded or something. When i click run in terminal, nothing happens.

:o

---

### Post by enarsee on 2008-12-12
BUMP again

---

### Post by meindian523 on 2008-12-12
rudihawk meant Right click on it,go to properties>>permissions and tick allow executing file as a program.then run it.You can't run .exe files except under wine.

Please specify which Realtek LAN card you have.Also,are you trying to access a Wireless network?If so,try a wired network first.Realtek cards usually don't have a problem working with Linux.

---

### Post by enarsee on 2008-12-13
> **meindian523 said:**
> rudihawk meant Right click on it,go to properties>>permissions and tick allow executing file as a program.then run it.You can't run .exe files except under wine.

Please specify which Realtek LAN card you have.Also,are you trying to access a Wireless network?If so,try a wired network first.Realtek cards usually don't have a problem working with Linux.

That is already ticked
Ok. i found a way to run it.

sudo sh [file name]

but then it gives me error
"U appear to be running X server. Please close it before continuing."

---

### Post by enarsee on 2008-12-13
BUMP again

---

