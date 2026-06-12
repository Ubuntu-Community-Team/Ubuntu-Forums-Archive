---
title: "Talking to the Smart Battery via SMBus?"
date: 2011-02-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MrPolite on 2011-02-14
Hi all,
I have 2 old dell laptops, one is Inspiron E1505, and the other is Inspiron 6000.
I want to see if I can send SMBus commands to the battery on either one of these laptops, but so far I've had no luck locating the SBS.

I've used lm-sensors and after loading i2c-dev/i2c-i801 I can see "a" SMBus link, but there is no battery on that link (supposed to be at address 0xB). 

Does any one have any ideas how the smart battery system is connected on a typical Dell system, such as the ones I have?

---

### Post by gabiz_ro on 2011-02-28
Don't know if this will help you.
I have take a look on few Dell schematics (Inspiron 6400,9300,9400) and on all of this battery is marked as SMBUS address 16h

What you want to do with commands sent via smbus?
Most Dell batteries of this laptops are based on Texas Instruments BQ2085 family an chip is sealed (protected) unless you know password to unseal them.

Also according to schematics,a list of SMBUS addresses
DIMM 0  A0h
DIMM 1  A4h or A2h
Inverter 58h
Charger 12h
CLK Gen D2h
Guardian 5Eh

---

