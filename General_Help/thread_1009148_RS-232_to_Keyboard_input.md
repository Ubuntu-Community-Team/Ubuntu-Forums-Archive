---
title: "RS-232 to Keyboard input"
date: 2008-12-12
forum: General Help
---

### Post by PaulusEm on 2008-12-12
Is it possible to write the output from a bar-code scanner (RS-232 serial port) as keyboard input?
The scanner which im using here is using a RS-232 serial port, for windows there are many applications which can do this, but i cant find any..

I hope somebody can help me out.. :)

-Paul

---

### Post by gpsmikey on 2008-12-12
Well, you can do things like "cat /dev/ttyb0 > somefile" for example (assuming ttyb0 is the port it is connected to and the baud rate etc is set right) to capture the data from the port to a file.  You can also assign the port to std in, however, unless the output from the scanner is in a format that is exactly the commands to make the OS do what you want (very unlikely), you will need some sort of utility that reads the data from the port then acts on it.  This is probably what you are looking for, but to answer your original question as stated, yes, it is possible to assign the serial port as keyboard input.

mikey

---

### Post by PaulusEm on 2008-12-12
Thanks for your reply, however cat /dev/ttyS0 gives no output for me. But when i use a sniffer on that port its reading the data.
I want to use this scanner for OpenBravo POS, normally i should use a keyboard wedge cable, however we've ordered a wrong scanner so we are trying to fix this without a cable first.

I've also tried to make a InputDevice of my scanner in the xorg.conf file, but that didn't work.

Hope there is still a way to solve my problem :)

---

### Post by gpsmikey on 2008-12-12
If something is "reading" that port, you need to figure out what it is.  Is there a loging associated with it?  I know on my machine, if I do a "cat /dev/ttyS0" I get the periodic messages my hot tub controller sends out (and since it is off, it is only 40 degrees F right now ... brrrrr !! ).  As I said, if you need it do do something more than simply copy the data from the port, you are going to have to find a utility or write one to deal with the data from the serial port.  Make sure the baud rate is set right - mine is running 9600 so I didn't have to play with it.

mikey

---

### Post by PaulusEm on 2008-12-13
I've google'ed alot already, but couldn't find any usefull applications.
I think it's not even possible to send keys to the keyboard(buffer) if I'm right, since there are so many applications for this on Windows, why not for linux(ubuntu)?

---

### Post by gpsmikey on 2008-12-13
Generally, any sort of barcode interface is only the "tip of the iceberg" as it were - it is usually the front end for entering data into a database and any other sort of inventory control system etc.  All those pieces need to play together for any of them to be useful.  I guess that nobody has yet to feel compelled to write that sort of application on the Linux side (or you have not been able to find them yet).  There may be other barcode readers out there with linux packages supporting them, but they are probably part of a package deal.  You may just have to write the utility you need on your own to run under linux or possibly you could run a windows utility under wine.  I have not played with wine at all, so I have no more information than that on it.

mikey

---

