---
title: "Modem Driver Compiled... but what now?!"
date: 2006-01-15
forum: General Help
---

### Post by metzger on 2006-01-15
Okay, I have a Lucent WinModem installed on my machine, and I have compiled the driver so that the system recognizes it and can utilize it. Now though, I do not now how I am supposed to connect to the internet. I know, dial-up, but it is all I can use right now. So, I opened up pppconfig and made an ISP profile. Now whenever I try to connect through **pon mcleodusa** (my service provider is McLeodUSa and that is also my ISP profile I set up), it just sits there, and I have waited for a while, and tried to open up google and other sites, and it says it was unable to connect. So, I am completly lost. Please help me if you can, I would really appreciate it.

---

### Post by StefanoCole on 2006-01-16
Type "sudo pon mcleodusa"
If you get nothing or if you run into trouble, open another terminal and do:
sudo tail -f /var/log/messages

This may give you an up-to-the-second idea of what is going on. Post the result in your question to the forum. I am not sure I can help you, but maybe from the log someone else will be able to give you any hints.

Other possibility:
WVDIAL

Install wvdial if it is not already installed. Some people have said that pppconfig worked better than wvdial while some have said that wvdial was the only utility that could get them on the net. Go figure.

type
wvdialconf .wvdialrc

enter your info and type wvdial to get on the net.
You can also use pon.wvdial and poff.wvdial.

Stefano

---

### Post by steve.horsley on 2006-01-16
I used a driver for a conexant winmodem once. It created a new serial device in the /dev/directory - can't remember the exact name. But this was the device I had to use as the serial port in the dialer configuration (instead of ttyS0 I used something like /dev/ttySHCFMODEM). Maybe you could look for a tty device like that, that the driver installed?

---

### Post by towsonu2003 on 2006-01-16
for wvdial, you can find more info in second link in my signature. 

to my knowledge, configuring wvdial is: ```
sudo apt-get update
sudo apt-get install wvdial
``` while you have your install cd in your drive and than  ```
sudo wvdialconf /etc/wvdial.conf
``` here wvdial should see your modem
```
sudo gedit /etc/wvdial.conf
``` and input your isp information, save&close, than ```
sudo wvdial
``` will dial up and connect (hopefully). let the terminal stay there until you're done,and disconnect with ctrl+c.

---

