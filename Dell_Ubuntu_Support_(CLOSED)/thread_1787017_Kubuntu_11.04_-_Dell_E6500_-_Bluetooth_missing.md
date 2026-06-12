---
title: "Kubuntu 11.04 - Dell E6500 - Bluetooth missing"
date: 2011-06-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by swappa on 2011-06-20
Did a fresh install of Kubuntu 11.04.
Everything is fine and dandy, but bluetooth is not working. 

<warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
src/main.c:parse_config() Key file does not have key 'DeviceID'
Unable to get on D-Bus

Trying to start ;

$ service bluetooth status
 * bluetooth is not running
$ service bluetooth start
 * Starting bluetooth                                                     [ OK ]
$ service bluetooth status
 * bluetooth is not running

The bluetooth radio is not active, so it hasn't been picked up. 

Any ideas?

---

### Post by swajime on 2011-12-04
I'm still looking for the same answer, but I notice you are not running service as root.  You need a sudo:

$ sudo service bluetooth start

john

---

