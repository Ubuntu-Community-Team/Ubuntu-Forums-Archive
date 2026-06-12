---
title: "wireless adapter not working in Ubuntu?"
date: 2011-02-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kuro114 on 2011-02-01
Hi,
I have a dell xps m1330. Decided I wanted to try Ubuntu, so I downloaded it. Really like it, however still kept windows vista around. I go in between them since I need a lot of microsoft programs for school and such. But recently, my wireless internet doesnt work in Ubunutu. It will work perfectly find in windows but my adapter isnt picking anything up. I looked around, found out how to see if the adapter is there. Ubuntu sees the adapter but for some reason its not working. Anyone have any idea how to solve this?

thanks!
-Jon

oh and a wired connection works

---

### Post by anglican on 2011-02-02
> **kuro114 said:**
> Hi,
I have a dell xps m1330. Decided I wanted to try Ubuntu, so I downloaded it. Really like it, however still kept windows vista around. I go in between them since I need a lot of microsoft programs for school and such. But recently, my wireless internet doesnt work in Ubunutu. It will work perfectly find in windows but my adapter isnt picking anything up. I looked around, found out how to see if the adapter is there. Ubuntu sees the adapter but for some reason its not working. Anyone have any idea how to solve this?

thanks!
-Jon

oh and a wired connection worksHave you installed wifi-radar? It's a handy package to find and configure available networks. It should show if your adapter really isn't picking anything up.

H

---

### Post by kuro114 on 2011-02-02
> **anglican said:**
> Have you installed wifi-radar? It's a handy package to find and configure available networks. It should show if your adapter really isn't picking anything up.

H


I just installed it and at the bottom of it theres a message saying not connected. so does that mean ubuntu isnt recognizing my driver or my driver just isnt responding?
Cheers,
jon

---

### Post by anglican on 2011-02-03
> **kuro114 said:**
> I just installed it and at the bottom of it theres a message saying not connected. so does that mean ubuntu isnt recognizing my driver or my driver just isnt responding?
Cheers,
jonBut is it showing a list of available access points?

H

---

### Post by TBABill on 2011-02-03
Was this device ever working for you in Ubuntu? If not, can you type the following into a terminal and paste the output back here to get some help setting it up? ```
lspci
``` and ```
sudo lshw -C network
``` and ```
iwconfig
``` and ```
lsmod
``` That last one is LSMOD in lower case, not ISMOD.

---

### Post by anglican on 2011-02-04
> **TBABill said:**
> ```
iwconfig
```Assuming iwconfig shows a wireless interface e.g. wlan0 you could also try ```
sudo iwlist wlan0 scan
```as well.

H

---

### Post by Jagoly on 2011-03-13
Didn't dell stuff used to be Linux certified? That'd be awsome...

---

