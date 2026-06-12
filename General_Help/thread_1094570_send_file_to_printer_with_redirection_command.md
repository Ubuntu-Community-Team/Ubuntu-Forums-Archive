---
title: "send file to printer with redirection command"
date: 2009-03-12
forum: General Help
---

### Post by mark bower on 2009-03-12
i am trying to work towards bluetooth communication from USB dongle to BT-200 (which is connected to parallel port on HP Laserjet4 printer).  i am trying to follow directions given by eduardoflores.  in WINXP using bluesoleil, printing to printer wirelessly worked just fine.  working with Ubuntu, below are the baby steps taken to talk to the printer, but a problem at step #4.  my dongle with $sdptool search sp 00:08:F4:23:28:71 sees the BT-200 just fine.

1) create a virtual serial port:
$sudo gedit /etc/bluetooth/rfcomm.conf

then type

rfcomm0 {
bind yes;
device 00:08:F4:23:28:71;           comment the MAC addr of my BT-200 @ printer
channel 1;
}

2) start the serial port
$sudo rfcomm bind 0

3) verify the creation of the serial port named "rfcomm0" 
$ls /dev/rfcomm0

result: "/dev/rfcomm0" is displayed in yellow on black - so far so good. 

4) now i try and send the text file BTtest.txt (on the Desktop) to the printer.

cmd line:  $cp BTtest.txt > /dev/rfcomm0

result:  cp: missing destination file operand after 'BTest.txt'

so what is wrong with the syntax on cmd line given in 4) that generates the operand error msg.  cp --help did not help me.  i recall in dos sending output to printer as something like file > prn.

---

### Post by mark bower on 2009-03-13
bumped.  any help please.

---

### Post by mark bower on 2009-03-13
bumped a 2nd time for response.

---

### Post by mark bower on 2009-03-22
bumped 3rd time hoping for help.  i included more info in original post

---

