---
title: "Can not enable desktop effects."
date: 2009-06-01
forum: General Help
---

### Post by snesxone on 2009-06-01
Im running 9.04, using an nVidia 6200 graphics card, and i can not for the life of me get desktop effects to enable. I have tryed everything i can think of, and mostly everything i have found through google. nothing seems to work. anyone capable of helping? :p

---

### Post by Kareeser on 2009-06-01
Have you tried enabling the proprietary drivers in the System -> Administration -> Hardware Drivers menu?

---

### Post by Jazzy_Jeff on 2009-06-01
Do you have the nvidia drivers installed for your card? Goto System > Administration > Hardware Drivers and see if it lists a driver for you.

---

### Post by snesxone on 2009-06-01
Yeah, i have that. I had the 180 driver, and it didnt work. So i tryed the 96 driver, becuase of [http://ubuntuforums.org/showpost.php?p=4915396&postcount=11](http://ubuntuforums.org/showpost.php?p=4915396&postcount=11)

and that didnt work either. I think my computer is just angry with me. What works for everyone else is not working for me.

---

### Post by Steelmourne on 2009-06-01
Manually install the drivers from the nvidia website. I'll be posting a guide about manually installing nvidia drivers step by step tomorrow. Basically, download the drivers, log out of Ubuntu, bring up a virtual console by ctrl+alt+1, log in from there and run the drivers from there.

---

### Post by MichaelSammels on 2009-06-01
Also look for the nVidia Server Settings application in synaptic.

---

### Post by snesxone on 2009-06-02
> **Steelmourne said:**
> Manually install the drivers from the nvidia website. I'll be posting a guide about manually installing nvidia drivers step by step tomorrow. Basically, download the drivers, log out of Ubuntu, bring up a virtual console by ctrl+alt+1, log in from there and run the drivers from there.


Okay, i will try that. Thanks, ;)

---

### Post by rcayea on 2009-06-02
On my old system which I had until about two weeks ago, I could never get the Nvidia 6200 card to work with the extra Desktop Effects. Even with a manual install of Nvidia's released drivers.

---

