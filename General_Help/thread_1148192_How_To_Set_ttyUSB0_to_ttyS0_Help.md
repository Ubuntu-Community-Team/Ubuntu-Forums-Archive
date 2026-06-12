---
title: "How To Set ttyUSB0 to ttyS0 Help???"
date: 2009-05-04
forum: General Help
---

### Post by link194 on 2009-05-04
hi,,,,

last few day i'm reading all open topic's but i'm lost a bit sorry.... regarding this  i hope any one can help me this problem....

 3455.900028] usb 6-1: new full speed USB device using uhci_hcd and address 4
[ 3456.067201] usb 6-1: configuration #1 chosen from 1 choice
[ 3456.070174] pl2303 6-1:1.0: pl2303 converter detected
[ 3456.082240] usb 6-1: pl2303 converter now attached to ttyUSB0
[ 3464.780028] usb 6-2: new full speed USB device using uhci_hcd and address 5
[ 3464.946592] usb 6-2: configuration #1 chosen from 1 choice
[ 3464.949556] pl2303 6-2:1.0: pl2303 converter detected
[ 3464.961627] usb 6-2: pl2303 converter now attached to ttyUSB1
[ 3471.030041] usb 7-1: new full speed USB device using uhci_hcd and address 4
[ 3471.197178] usb 7-1: configuration #1 chosen from 1 choice
[ 3471.200150] pl2303 7-1:1.0: pl2303 converter detected
[ 3471.212198] usb 7-1: pl2303 converter now attached to ttyUSB2
[ 3480.780028] usb 7-2: new full speed USB device using uhci_hcd and address 5
[ 3480.946503] usb 7-2: configuration #1 chosen from 1 choice
[ 3480.949464] pl2303 7-2:1.0: pl2303 converter detected
[ 3480.961532] usb 7-2: pl2303 converter now attached to ttyUSB3

i'm using ubuntu 8.10

all my devices working fine in all cominacation..........

my problem is  >>> i have 4 reader loger attached this 4 ports  ttyUSB0-1-2-3  they working fine also ......but when my pc boots or i restart all the ttyusb they will change,,,

e.g:

if ttyusb0--->on reader 1  after boot that reader will start on  ttyusb3///////  after pc restart's or boots ttyusb they will change all mixed up......

for now only way to solved my problem is  i do this after pc boots or restarts....

i will disconnect all usb-serial cables from the pc and i will connect them after each other again 

e.g: ttyUSB0 ---->willbe  reader 1
       ttyUSB1----->willbe  reader 2   and so on   

like this when i run the readers  they start how should be.....now i dont know if there's a way to start connected device's starts or lock on the readers.....???????

or there's way to set  ttyUSB0  to ttyS0.....

thx for help...

---

### Post by bgrattan on 2009-06-01
Sorry, this is not an answer because I have the same question.

I have two (2) PL2303 Serial Ports which need to be ttyUSB0 and ttyUSB1.  They don't always come up in the same order with the same assignment.  How can I nail ttyUSB0 to a specific dongle?

Thanks.

Bob

Ubuntu 9.04

---

### Post by Sy3bol on 2010-06-10
hi folks,
sorry for the thread revival... but has anyone got a answer to this... i also have 4 usb dongles that run fine (comms a ok.) and i can telnet to the "console" via ser2net; but whenever a reboot/cold start happens the PNP enumeration messes up the ttyUSB* as they may not correspond to when i configured the ser2net conf file i.e. USB serial dongle on config maybe ttyUSB0 but on os start change to ttyUSB1 etc...

any one kind enough to pass some pointers how to statically map the  usb dongle based on which bus id etc its connected on to a ttyUSB line - so it remains constant.

peace.

---

### Post by LiquidMeson on 2010-06-10
The linux kernel is dynamic as people are, why stay static?

---

### Post by dcstar on 2010-06-10
[http://answers.oreilly.com/topic/678-how-to-configure-udev-for-a-usb-serial-port/](http://answers.oreilly.com/topic/678-how-to-configure-udev-for-a-usb-serial-port/)

[http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

---

