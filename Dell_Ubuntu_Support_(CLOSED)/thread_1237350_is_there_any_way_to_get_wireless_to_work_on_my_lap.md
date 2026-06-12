---
title: "is there any way to get wireless to work on my laptop"
date: 2009-08-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rhythmiccycle on 2009-08-11
i tried to get wireless to work on my inspiron 1300 before but could never get it to work. i also spoke to a friend of mine who had linux running on a dell laptop and he also tried all types of things but could never get it to work.

is trying to get wireless to work on a dell laptop a hopeless cause?
Have any of you gotten it to work on one?

---

### Post by ugm6hr on 2009-08-11
Yes.  Wifi works on most Dell laptops.  I have had 3 (Dell Mini 9, Dell Insiron 5000e+PCI wifi card, Dell 500m), all of which connected just fine.

If you want to try and get it to work, you will have to install 9.04 Ubuntu, or boot from a LiveCd, and give us more detail.

---

### Post by rhythmiccycle on 2009-08-11
ok, i have ubuntu 9.04 installed on my laptop.

i left click on the bars by the clock and select "create New Wireless network..."

the network i'm currently trying to connect to is 

Security type: WPA2-Personal 
Encryption type: AES

so i select the wpa & wpa2 -personal

there is no option asking about encryption type.

so i type in the password, and then hit enter, 

and a message pops up near the clock up top, that says "not connected"

i'm used to windows where there is a list of networks to choose from, but i can't find any list.

what should i do?

---

### Post by Whiffle on 2009-08-11
There should be a list of networks that pops up when you click on the bars next to the clock, and then you should be able to select the one you want from that, and then it will prompt you for your login information.

But, since its not doing that, I guess your wireless isn't quite working right.  First of all, is there a switch that turns on your wireless, and is it on?  (gotta check the simple stuff first ;) )

Next, could you open up a terminal (Applications > Accessories > Terminal ), and post the output of these commands

"sudo iwconfig" and "sudo lspci -v"  

You can paste into the terminal with ctrl+shift+v and copy from it with ctrl+shift+c , and then put everything into the [ code ] tags here on the forum.

---

### Post by ugm6hr on 2009-08-12
> **rhythmiccycle said:**
> i'm used to windows where there is a list of networks to choose from, but i can't find any list.

As mentioned, if you can normally see your wifi access point in Windows, you should see it in Ubuntu too.

Useful info to give us: [http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)

But first, connect with a cable and check System -> Admin -> Hardware drivers

It is likely you need firmware to make your wifi wok properly, since most Dell laptops were either Intel (which should just work) or Broadcom.

---

### Post by rhythmiccycle on 2009-08-12
> **ugm6hr said:**
> A
But first, connect with a cable and check System -> Admin -> Hardware drivers

It is likely you need firmware to make your wifi wok properly, since most Dell laptops were either Intel (which should just work) or Broadcom.

i next did that and activated the "Broadcom B43 wireless driver"

after that i updated every thing from the update manager, restarted the computer

AND NOW ITS WORKING!!!

thanks!

---

### Post by hetx on 2009-08-12
Grats, welcome to the free world :popcorn:

---

### Post by ugm6hr on 2009-08-12
> **rhythmiccycle said:**
> i next did that and activated the "Broadcom B43 wireless driver"

after that i updated every thing from the update manager, restarted the computer

AND NOW ITS WORKING!!!

thanks!

Wasn't so hard, was it?

Easier than installing most drivers on other OS, provided you know where to look...

---

