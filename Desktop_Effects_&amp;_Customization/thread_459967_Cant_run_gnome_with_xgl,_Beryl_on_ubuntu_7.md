---
title: "Cant run gnome with xgl, Beryl on ubuntu 7"
date: 2007-05-31
forum: Desktop Effects &amp; Customization
---

### Post by dahund on 2007-05-31
i have a laptop with an x1400 card. Apparently not a good thing, when you want beryl.  
So i follow the guide bellow from **Alternate method: Using closed source FGLRX drivers from ATI.**

[http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29)

after running the guide i try to change session to *gnome with xgl* and then log in.
The screen blinks a couple of times then goes back to login screen.. they only way i can log in is via gnome only..

when i open terminal an write beryl i get 

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
allan@allan-laptop:~$ 


can anyone please help. ;)

---

### Post by Ub1476 on 2007-05-31
I have the same card, beryl works. Tell me, when you installed Ubuntu, did X server start? And have you enabled the drivers in Restricted Drivers Manager?

---

### Post by dahund on 2007-05-31
No had af few problems with the driver in the begining, but it works now. used wiki to help me inst the driver.
yes the card is enable. the guide told me to enable it.:p

---

### Post by dahund on 2007-05-31
any idea guys..:o

---

### Post by Ub1476 on 2007-05-31
Well here's how it worked for me.. 

When i booted from the CD, X would not start so I followed this guide: [Linky]("http://ubuntuforums.org/showthread.php?t=448809&highlight=feisty+fawn")

Note that first I tried this guide: [Linky]("http://ubuntuforums.org/showthread.php?t=414194"). But the drivers didn't enable 3d and so on, which meant I couldn't use beryl etc.. So I reinstalled following the guide above.

After that I followed same guide as you.

A friend of me has X1400 too, but with 256mb and 512 extended. He had no problems with X and also followed the same guide as you.

I have X1400 128mb and 512 extended..

So I don't get why it doesn't work with you..?

---

### Post by dahund on 2007-05-31
i think i will start all over to many inst on top off each other thx for advise :p

---

