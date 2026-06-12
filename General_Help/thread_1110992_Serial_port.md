---
title: "Serial port"
date: 2009-03-30
forum: General Help
---

### Post by nunojpg on 2009-03-30
I'm testing a serial connection between two computers.
The "master" have ubuntu and the other have openwrt.

I'm having some strange results with "echo" to the serial port, and as minicom works ok it looks that everthing is ok with the link...

tests:

1st:
openwrt: cat /dev/ttyS0
ubuntu: minicom

Result: everthing I write at minicom is displayed at openwrt after I hit return, as expected.

2nd:
openwrt: cat /dev/ttyS0
ubuntu: while true; do echo $'test\n' > /dev/ttyUSB0; sleep 1; done

Result: "test" string is receved each second, but in about 10% of strings only one "\n" is printed, so they are print in adjacent lines(echo is sending another \n by itself"

3rd:
openwrt: cat /dev/ttyS0
ubuntu: while true; do echo $(date)$'\n'; sleep 1; done

Result: Nothing is printed until I stop the while loop and do something like "echo $'test\n' > /dev/ttyUSB0", then all the "date" strings appear at openwrt(without any new lines)

---

