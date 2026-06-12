---
title: "Networking help"
date: 2009-05-12
forum: General Help
---

### Post by Bearded-flower on 2009-05-12
Ok i have intrepid (easy peasy), and XP installed on my netbook and i want to install jaunty over the whole hard drive using a live CD.
but first i need to back up some files.
I was going to set up a network with this oooooooold HP we have.
i was gunna transfer the files to that, install jaunty and transfer the files back to my netbook.
but i tried and i cant figure out how to.
I as using blue networking cable and plugged it into both and nothing.
What am i doing wrong what do i have to do?

---

### Post by hexanol on 2009-05-12
You are saying that you have two PC connected directly via a simple "ethernet cable" (i.e. no other device between the two) ? If it's right, you'll have to set up IP address manually for both computer, or it won't work.

Also, I'm not totally sure about this one, but depending on the type of "ethernet cable" you have (patch vs crossover cable) and the network interfaces in your computer (do they both support Gigabit ethernet, aka 1000BASE-T?), it will never work because of a problem at the "physical level".

---

### Post by Bearded-flower on 2009-05-12
Uuum i dont actuly know anything about the ethernet cable, its long its blue and it belonged to my school!
RELAX im going to return it!
i was only gunna borrow it for the night.
anyway how do i set up an IP adress?

---

### Post by hexanol on 2009-05-12
Well, if the cable was plugged from a computer to a hub/switch, then it's a patch cable, and you won't be able to use it to connect your 2 computers directly without an adapter. And if the cable was plugged from a computer to another computer, then there's high change (but it's not even sure) it's a crossover cable, and you'll be able to use it. If you don't know where it was plugged, then it's mostly a patch cable. And if it's a patch cable, like I said, it's useless in your situation without a crossover adapter (or I don't know how they call it).

To set up an IP address manually in Linux, you can either do it with "ipconfig" commands (see man ipconfig or search on the web for "static ip address linux") or within NetworkManager...

---

