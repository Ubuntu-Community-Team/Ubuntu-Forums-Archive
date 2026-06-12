---
title: "NOOB ALERT &lt;&lt;need help with 1520 laptop wifi"
date: 2008-06-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Deanouk87 on 2008-06-11
hey all... 

ill open this saying im a complete noob at linux, and installed ubuntu (via wubi, 8.04 hardy on a 15gb partition)for a bit of fun, and to experiment.loving it so far, apart from lack of wifi.

i have installed my windows driver via ndiswrapper, but wifi is still not working, and a bit confused on what to do next... also the device light is not active, nothing happens when i reboot.

i have done full updates to the system, through a wired connection.

the adapter in question is "dell wireless 1505 draft 802.11n", after a bit of googleing, its a "broadcom"

i have tryed searching, but there is alot of jargon in other posts, and they either dont make much sense to me, or advise to use shortcuts/commands that i have no idea what to do.:(

still, its only been 4 hours since it was installed... gonna try an not use windows for at least a week to see how i get on once wifi is up.

cheers guys :KS

DeanoUK

ps... any idea if its possible to use mobile internet from a sony ericsson phone?

---

### Post by lisati on 2008-06-11
[LIST=1]
[*]Is your wireless connection showing up when you type ```
iwconfig
``` in a terminal window?
[*]I have an older Sony Ericsson phone which came with its own web browser, which connects through my mobile carrier's service. There are possibilities.
[/LIST]

Hope these help you on your search for answers to your wuestions.

---

### Post by Deanouk87 on 2008-06-12
hey, 

in responce to the wifi, it says the following when i type iwconfig into terminal...

```
dean@dean-laptop:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



dean@dean-laptop:~$ 

```



as for the sony ericson question, i dont think i typed it properly.

i get free data with my mobile carrier, and would like to use my phone as a modem for when i take my laptop on travels. i use this quite often with vista, but all through sonys own pc suite... idealy i would like to do that via bluetooth...  but ignore that, ill deal with that once i get normal wifi sorted :)

---

### Post by sagarun on 2008-06-12
> **Deanouk87 said:**
> hey, 

in responce to the wifi, it says the following when i type iwconfig into terminal...

```
dean@dean-laptop:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



dean@dean-laptop:~$ 

```



as for the sony ericson question, i dont think i typed it properly.

i get free data with my mobile carrier, and would like to use my phone as a modem for when i take my laptop on travels. i use this quite often with vista, but all through sonys own pc suite... idealy i would like to do that via bluetooth...  but ignore that, ill deal with that once i get normal wifi sorted :)

Check this link...here is a way to get data from modem.....


[http://arun-sag.blogspot.com/2008/06/airtel-gprs-linux-way.html]("http://http://arun-sag.blogspot.com/2008/06/airtel-gprs-linux-way.html")



and for your wi-fi...

click system->administration->hardware drivers

if u can see the modem drivers then its ok...also run a hardware test....

And try adding linux backport modules in your software respositories list....
then do : sudo apt-get update
$ sudo apt-get install linux-backports-modules-2.6.24-16-generic
(note change the linux kernel version according to yours)
and also try the bellow link....

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Known_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Known_Issues)


I don't know about ndiswrapper....

---

### Post by Deanouk87 on 2008-06-12
> and for your wi-fi...

click system->administration->hardware drivers

if u can see the modem drivers then its ok...also run a hardware test....

And try adding linux backport modules in your software respositories list....
then do : sudo apt-get update
$ sudo apt-get install linux-backports-modules-2.6.24-16-generic
(note change the linux kernel version according to yours)
and also try the bellow link....

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Known_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Known_Issues)


I don't know about ndiswrapper....
that link didnt help much, got a few messages while trying it, like files not found. and just my nvidia drivers in the system>admin>hardware section.

ill try adding linux backport modules in the software repositories list... i have no idea how to do this though :(

---

### Post by sagarun on 2008-06-13
> **Deanouk87 said:**
> that link didnt help much, got a few messages while trying it, like files not found. and just my nvidia drivers in the system>admin>hardware section.

ill try adding linux backport modules in the software repositories list... i have no idea how to do this though :(

To add restricted respositories...just goto Administration->software sources
 
under ubuntu software tab....click the third and fourth check box "Proprietary drivers for devices"
"software restricted by legal issues"


Will you please post the messages  you got while you tried that link...?

---

### Post by Deanouk87 on 2008-06-13
> **sagarun said:**
> To add restricted respositories...just goto Administration->software sources
 
under ubuntu software tab....click the third and fourth check box "Proprietary drivers for devices"
"software restricted by legal issues"


Will you please post the messages  you got while you tried that link...?

Yeah, ill give it a go when im back from work. Slowly getting used to this stuff! Cheers for the help guys, think that link was mainly for upgrading from 7.04 to hardy. Ill do that again first an let you know what it says.

---

