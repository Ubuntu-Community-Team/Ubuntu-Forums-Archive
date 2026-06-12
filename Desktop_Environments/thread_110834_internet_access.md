---
title: "internet access"
date: 2005-12-31
forum: Desktop Environments
---

### Post by johnfs on 2005-12-31
i just installed ubuntu 5.10 and everything is good.How do i set up my isp on ubuntu to access the internet?:rolleyes:

---

### Post by super on 2005-12-31
what kind of internet do you have? high-speed or dial-up?

---

### Post by johnfs on 2005-12-31
sorry it is dial up

---

### Post by super on 2005-12-31
too bad, dial up is a bit harder than high-speed. :( 

try this first: system->administration->networking. select 'dial-up networking/ppp' and click 'configure'. you should be able to just fill in the information. when it asks for a location of the modem the most common is /dev/modem. the critical part is if your modem is supported by linux or not. many '[win/softmodems]("http://en.wikipedia.org/wiki/Winmodem")' are not.

if your modem is a softmodem it gets a bit trickier.
visit '[linmodem]("http://linmodems.org/")' for supported modems and their drivers. download and install with the given instructions. if that still doesn't work, download '[scanmodemhere]("http://linmodems.technion.ac.il/packages/scanModem.gz")'  (you may need to download this in windows then copy it in linux) and run it from the terminal.

it will report the make of modem in the file called modem**.txt in the same place where ur scanmodem script is.

If u cant still make out, send them your modems1.txt to [http://linmodems.technion.ac.il/first.html](http://linmodems.technion.ac.il/first.html) and they can give you better instructions.

---

### Post by vasudevank on 2005-12-31
try to switch to high-speed it will save a lot of time

---

### Post by johnfs on 2006-01-01
thank you very much super.i have it working now.:p

---

