---
title: "best program for displaying cpu temp and fan speed?"
date: 2013-10-04
forum: Desktop Environments
---

### Post by mystmaiden on 2013-10-04
I just put together a computer with N-Alvorix-RS880-uatx mainboard and an amd athlon 2 quad core cpu (running 64 bit Precise LTS). There is a bit of a bug that gives me a system fan failure warning on startup even though the fans are all humming along nicely. One suggestion I read was to leave it as is and monitor the temps and fan speeds before taking a chance on bricking the motherboard with a bios update. I've never done a bios flash so I'm all for that. My question - is conky the best program for that? I was looking through a conky thread just now and it all looked really complicated.

Thanks,

mystmaiden

---

### Post by ibjsb4 on 2013-10-04
Conky can be set up to monitor everything and more, then [display it]("https://www.google.com/search?q=conky+pictures&client=ubuntu&hs=nR6&channel=fs&tbm=isch&tbo=u&source=univ&sa=X&ei=arpOUs6JGYn-9QTVnoGwDQ&ved=0CC4QsAQ&biw=870&bih=830&dpr=1.09") on your desktop.  There are many monitor packages, I do not us any desktop packages but look [here]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=temp+cpu+monitor&sa=Search&cof=FORID:9").

---

### Post by mystmaiden on 2013-10-04
Thank you ibjsb4 for the links. I'd never seen google ubuntu page before, pretty cool. I'd be fine with having conky available and not constantly displayed but just where I could check it regularly.

---

### Post by slickymaster on 2013-10-04
There's [Psensor]("http://wpitchoune.net/blog/psensor/") which can monitor the motherboard and CPU temperatures, the temperature of Nvidia GPUs, hard disk drives temperature, fan speed and CPU usage. It can also display hot temperature alerts using desktop notifications and the application indicator which turns read when a threshold is reached. The alerts are not enabled by default though and have to be enabled.
T o install it, firstly you need to install lm-sensors and hddtemp as these packages are required for Psensor to be able to monitor CPU, hard disk and motherboard temperatures as well as CPU fan speed:```
sudo apt-get install lm-sensors hddtemp
sudo sensors-detect
sudo service module-init-tools start
```After that install Psensor itself:```
sudo add-apt-repository ppa:jfi/ppa
sudo apt-get update
sudo apt-get install psensor
```

---

### Post by buzzingrobot on 2013-10-04
Various little GUI's of one shape or another are available to display temperature and fan speed.  I don't like the looks of any of them, and I don't need to have a constant display of that info.  As far as i can tell, they all depend on lm-sensors to actually collect the data they display.

So, I install lm-sensors, run sensors-detect (required) in a terminal, and then when I do want to check on things, run "sensors" in a terminal.

---

### Post by mystmaiden on 2013-10-07
thank you slicky and buzzingrobot for the replies. When running sensors-detect are the default replies the ones that are in all caps? Lots of questions there and I really don't want to mess this up.

---

### Post by buzzingrobot on 2013-10-07
Yes, the all-caps options are the defaults.

---

