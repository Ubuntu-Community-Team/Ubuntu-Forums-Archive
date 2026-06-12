---
title: "Networking Problems"
date: 2009-01-17
forum: General Help
---

### Post by Arukas on 2009-01-17
I am having trouble networking, and never setup a network before.

Basically my setup, is plugging two computers up into a switch.  I have no clue where to go from there.  Neither computer recognise the presense of the other computer.


Now, I've tested the hardware and cables and there's no problem there.  I'm sure I'm not setting something up or doing something totally wrong in the first place.

---

### Post by stefangr1 on 2009-01-17
First: I assume both computers aren't connected to the internet?

There are different ways to achieve this. You could setup one of the computers as a server and the other as a client, I won't go in to that.

I think the easy way would be to open the network manager in both computers, and assign both an ip address in the same subnet, like: 192.168.1.2 and 192.168.1.3. Then the computers should already be able to see each other.

---

### Post by x22 on 2009-01-17
> plugging two computers up into a switch

we really need more info to help you: OS info, netcard
type...is the switch itself receiving a signal frm the
net, or are the computers to connect to one another
only?  If the latter, the easier way is with a
crossover cable--no switch.

in any event, are the cards being recognized by the OS?
try "ifconfig" and see what comes up: eth0 or eth1.
if so, depending what yr setup is, you should be good
tp go...is not "lspci" to see whether the bus
recognizes yr cards. Then drivers may need
finding/installing, it all depends.
 
> tested the hardware...there's no problem...

how was this established?

---

### Post by Arukas on 2009-01-17
Until I get my gateway computer setup, only one of my computers can connect to the network, from what I understand.  

Since you are assuming, I'm not using the internet in the network, which is correct for now.  I'm just trying to go with simplicity.  However, if I try to plug my cable modem into the switch, can I setup one computer to use it, since only one can use it?  


Also the reason I know my hardware works, is tested with plugging the modem directly into the computer and seeing if i could use into the Internet.  And I"m using ethernet cards.

---

### Post by minsf on 2009-01-17
lets call your two computers A and B from now on.
1. Does computer A have ubuntu 8.10?
2. assuming yes to #1, please go to terminal in computer A (Applications>Accessories>Terminal), and enter ```
sudo lshw -C network | less
``` you may be asked for your password. if the output is too long to fit the screen you can scroll with the arrows. you quit it by pressing q. please cut and paste output here (to cut use ctrl+SHIFT+c, rather than ctrl+c). 
3. if yes to #1, in the terminal of computer A enter ```
ifconfig | less
``` and post the output here. again you may need to scroll down if the output is too long.
4. Does computer B have ubuntu 8.10?
5. if yes to #4, repeat step 2 for computer B.
6. if yes to #4, repeat step 3 for computer B.

---

### Post by Arukas on 2009-01-18
Just so no one else post.  I am changing my network configuration, and its different from what I was originally was doing.  I started at the wrong end.

---

