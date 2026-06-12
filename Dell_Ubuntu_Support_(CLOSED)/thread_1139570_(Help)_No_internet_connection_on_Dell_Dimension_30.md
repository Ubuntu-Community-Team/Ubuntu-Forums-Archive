---
title: "(Help) No internet connection on Dell Dimension 3000"
date: 2009-04-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mrparadigm on 2009-04-27
[SIZE=2]           I am new to linux but very familiar with computers and have installed 9.04 i386 on a [/SIZE][SIZE=1][SIZE=2]Dell Dimension 3000 Desktop. Everything has loaded fine accept that it will not connect to the Internet. The desktop would be connected by Ethernet to a Motorola dsl router from ATT (non wirless). The router works because this is was written using that same connection on a laptop also using 9.04. What information do you need from me to help remedy this problem?[/SIZE]

[SIZE=2] 
:smile:Any help would be greatly appreciated as I have just converted my parents to Ubuntu because of all the problems they had with Windows![/SIZE][/SIZE]

---

### Post by armandh on 2009-04-27
with the same cable that runs ok with the laptop.......

some times it is as simple as clicking on the connection icon and enabling the etho-0. 

things I have found wrong that were head scratchers

a cable with tr/rc flipped and the computer under test without a self sensing nic. [assuming fixed at the hub]

lightning damaged nic. tested good from the computer side

on-board nic disabled in bios or interrupt provisions

lightning damaged pci slot [interrupt bad]

unsupported nic.

---

### Post by creolbuay on 2009-04-30
Have you tried setting your network up via command line?

Log into terminal run

edit: /etc/network/interfaces

Make an entry as follows if it's not in there already:

address xx.xx.xx.xx
netmask xx.xx.xx.xx
gateway xx.xx.xx.xx

save and exit from the file.
 restart networking 
/etc/init.d/ networking restart

That usually fixes my issues.

---

