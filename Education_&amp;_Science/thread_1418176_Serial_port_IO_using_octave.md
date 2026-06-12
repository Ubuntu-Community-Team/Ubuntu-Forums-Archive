---
title: "Serial port I/O using octave"
date: 2010-02-28
forum: Education &amp; Science
---

### Post by eeprom on 2010-02-28
Hello,
I am new to linux and octave.  I have an older computer with a serial port.  I know that with matlab I can use a microprocessor board to send/receive information from matlab to the port and vice versa.  Does anyone have some sample code in octave which demonstrates how to do this?

Also, windows has (used to have) a hyperterminal program, which was also a good means of reading data from an external serial device.  Windows has discontinued this (maybe because it worked) as of Vista.  Anyway, what is the linux version of hyperterminal?

thanks,
EE

---

### Post by ssam on 2010-02-28
minicom is probably what you want for sending receiving via serial port. (it also has things for dialing a modem, but you can disable this).

not sure about octave, but if you are not bound by having existing code you could look at using python. pyserial lets you talk to a serial device, and numpy/scipy/matplotlib give you lots of numerical and plotting tools.

---

### Post by sprince09 on 2010-02-28
From [http://www.gnu.org/software/octave/FAQ.html](http://www.gnu.org/software/octave/FAQ.html), about 1/2 way down the page:

[I]Differences in core functions A large number of the Matlab core functions (ie those that are in the core and not a toolbox) are implemented, and certainly all of the commonly used ones. There are a few functions that aren't implemented, for example condest or to do with specific missing Octave functionality (gui, dll, java, activex, dde, web, and serial functions). Some of the core functions have limitations that aren't in the Matlab version. For example the sprandn function can not force a particular condition number for the matrix like Matlab can.
[/I]

Looks like no unfortunately :(

---

### Post by eeprom on 2010-03-01
Sprince09,
I see that Octave doesn't support serial I/O.  Do you know of another means of reading in serial data?  How about reading analog voltages from microphone port?  I know this can be done.  I just don't know how.

EE

---

### Post by aztk on 2010-08-31
Hey bro!
Check the following thread: [Serial Port for Octave - LibertadHack]("http://libertadhack.blogspot.com/2010/08/puerto-serie-para-octave-serial-port.html")
I made some scripts to communicate with the serial port in Octave through pySerial and sockets.

Sorry my bad English. :)

---

### Post by keithspg on 2010-11-03
> **aztk said:**
> Hey bro!
Check the following thread: [Serial Port for Octave - LibertadHack]("http://libertadhack.blogspot.com/2010/08/puerto-serie-para-octave-serial-port.html")
I made some scripts to communicate with the serial port in Octave through pySerial and sockets.

Sorry my bad English. :)

Just grabbed this. If I need it, I'll post as to how it works. I think I have it all set up and translated the script responses into English for our office. It seems to work.

The only thing is that I needed to edit the location of the py script to be a true link instead of ./ in the serial.m script.

KeithG

---

### Post by nocnokneo on 2011-06-29
The best serial port terminal for new Linux users is _not_ minicom. Look at gtkterm. To install on Ubuntu:

**sudo apt-get install gtkterm**

or simply hit **Alt+F2** then type **apt:gtkterm** in the run dialog that pops up.

---

### Post by vanangamudi on 2011-08-31
Here is program in C. u can pipeline the output to the program for transmitting thro' serial port. a simple bash script can do it.

[Serial Port manipulation in C]("http://yengal-marumugam.blogspot.com/2011/07/serial-port-manipulation-in-c-linux.html")

---

