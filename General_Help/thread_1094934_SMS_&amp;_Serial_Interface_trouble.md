---
title: "SMS &amp; Serial Interface trouble"
date: 2009-03-13
forum: General Help
---

### Post by kingpin303 on 2009-03-13
Hi,

I have a Siemens MC35i SMS modem connected to my Ubuntu machine through a serial interface.  I’m running a script that sends AT commands to the modem for the purpose of sending SMS.  Though I’m experiencing problems with this.  It seems like the commands are not properly sent.  The SMS modem works perfectly with a terminal emulation program but in this case that is not an option.

From the command line I try to send commands like this one :
echo AT+CSCA=0475161616 > /dev/ttyS0
To see what’s being sent out the serial interface I’ve set up another terminal window : cat /dev/ttyS0.
This is what I see when I send the above command (3 times in this case) : 
AT+CSCA=0475161616
AT+CSCA=04751

OK

616AT+CSCA=0475161616
A

OK

T+CSCA=04751616AT+CSCA=0475161616
A

OK

It seems like the commands are thrown out the interface. Rarely it succeeds to send a command properly.

I’ve tried to set the serial interface with the stty command like this :  stty 9600 cs8 –parenb – cstopb crtscts ixon > /dev/ttyS0
It didn’t make any difference.
Am I missing something here ? Should the serial interface be initialized in some different way.

Help is very much appreciated.

---

