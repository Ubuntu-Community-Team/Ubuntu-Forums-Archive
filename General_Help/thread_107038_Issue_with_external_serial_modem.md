---
title: "Issue with external serial modem"
date: 2005-12-22
forum: General Help
---

### Post by linuxfroggy on 2005-12-22
I would like to request some help regarding an external serial modem. I have managed thanks to the System/Network tool to connect and enter parameters to get the modem connected to internet but there is still a small issue : when ordering disconnection thanks to the Gnome applet, the modem does not hang up. Connection is broken but the line is still taken by the modem. I undertood from wandering around that the options file in /etc/ppp can be used to tweak a disconnect script thanks to chat for example but I must admit that few trials did not succed... I would really appreciate if someone could give me some hints on the subject.

Thanks a lot,

Linuxfroggy

---

### Post by jliedeka on 2005-12-23
You should be able to force the hangup AT code.  It's beena while since I've used a modem but the command to send it "+++ATH0" the three plusses are like an interrupt.

What I don't really remember is how to send that to a serial port.  You could try becoming root and cat the above code to your serial device, aka /dev/ttyS0 or whatever.  I think I used to do it with some terminal emulator but my memory is fuzzy.

As a more permanent solution, you probably want to check out you PPP configuration.  Is there anything in /etc/ppp concerning disconnect options?

---

### Post by linuxfroggy on 2005-12-24
Thanks for the reply.

Though using sudo, I have not been able to redirect any string to /dev/ttyS0. It seems that the ppp daemon is getting exclusive access though I do not understand what is the mechanism. Using chat has not been very efficient either... Regarding a disconnect option, it does exist in the options file under /etc/ppp, there is a line dedicated to that but trying to use a chat command just get the following poor result : no connection anymore. I'll carry on...

Linuxfroggy

---

### Post by jliedeka on 2005-12-24
It might help to run "sudo su" before doing the cat or echo command.

If you type "sudo echo "+++ATH0" > /dev/ttyS0", the stuff after the redirect isn't part of root's shell, it's part of yours.

Try:
sudo su
echo "+++ATH0" > /dev/ttyS0

(the device ttyS0 is assuming you are using the COM1 serial port, use tty S1 for COM2, etc)

---

