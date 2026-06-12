---
title: "Help with using serial port for data logging"
date: 2010-03-07
forum: Education &amp; Science
---

### Post by eeprom on 2010-03-07
Hello,
I'm running Ubuntu 8.04, and i have a serial data acquisition card which I want to read through my linux machine.  I need some very basic "getting started" concepts.

1.  How to open a serial port and verify that it is reading something?
2  How to change serial port settings?
3  Where in ubuntu can I view my ports?

FYI - I have minicom, and the manual in front of me.  It is, at this point, well over my head.  What I would prefer is a simple example showing how to get a device to talk to the port.

thanks for your help.

EE

---

### Post by hubie on 2010-03-07
Most things that deal with the serial port will use setserial.  You can look at the [manpage]("http://setserial.sourceforge.net/setserial-man.html") for it to see the options.

A few good places to start would be
[LIST]
[*][Serial HOWTO]("http://tldp.org/HOWTO/Serial-HOWTO.html")
[*][Some examples]("http://www.cyberciti.biz/faq/find-out-linux-serial-ports-with-setserial/")
[/LIST]

If you know a little Python, there is a nice interface to the serial port called [pySerial]("http://pyserial.sourceforge.net/").  The docs have some [example code]("http://pyserial.sourceforge.net/examples.html").  A short program that shows you how to read and write to the serial port can be found [here]("http://ayaz.wordpress.com/2007/06/11/serial-port-communication-on-slackware-using-pyserial/").  The code is presented for Slackware, but there doesn't appear to be anything in it that is Slackware-specific.

---

### Post by not_a_phd on 2010-03-07
Another excellent tutorial can be found at this link:

[http://www.easysw.com/~mike/serial/serial.html](http://www.easysw.com/~mike/serial/serial.html)

Regards.

---

### Post by eeprom on 2010-03-08
Thanks for the excellent references.  I have it running now.

EE

---

### Post by HDowns on 2010-11-30
I'm working on the same problem. Has anyone had any solution like AGG Software's [Data Logger]("http://www.aggsoft.com/serial-data-logger.htm") but for Ubuntu? I have used this application in the past on Windows and it meets all my needs, but I can't find similar app for my new OS.

---

### Post by douglaswood34 on 2010-12-03
I use the following set-up for monitoring temperatures via serial port.  I monitor temps from multiple sensors, and keep a file via rrdtool.  Check out this site.  I am sure you can do way more than just temps with the set-up there.....

[http://martybugs.net/electronics/tempsensor/](http://martybugs.net/electronics/tempsensor/)

---

