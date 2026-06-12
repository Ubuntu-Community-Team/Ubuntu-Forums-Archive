---
title: "Nvidia-xserver problems"
date: 2009-06-23
forum: General Help
---

### Post by Kcorb on 2009-06-23
Hello I am new to ubuntu and i got  friend of mine to install the driver for my laptop and the computer was updating and someone unpluged internet while i was doing updates and i just continued on not realizing it and when i restarted my laptop it went back to its crap resolution and I tried editing the nvidia settings but all it says is run as root the nvidia-xconfig file and restart it but i cant figure out how to do that can some one please help me it will be much apreciated

---

### Post by SteveDee on 2009-06-24
> **Kcorb said:**
> Hello I am new to ubuntu and i got  friend of mine to install the driver for my laptop and the computer was updating and someone unpluged internet while i was doing updates and i just continued on not realizing it and when i restarted my laptop it went back to its crap resolution and I tried editing the nvidia settings but all it says is run as root the nvidia-xconfig file and restart it but i cant figure out how to do that can some one please help me it will be much apreciated

Sorry if I've misunderstood your question, but I think you are referring to the "Nvidia X Server Settings" option in the System > Administration menu. If you run this application straight from the menu, you can view settings, but won't be able to save your changes because you must be root to do so. 

If this is your problem then open a terminal and type; gksu nvidia-settings
Now you will find any changes made can be saved.

---

### Post by fundakaraoglu on 2009-10-31
> **SteveDee said:**
> Sorry if I've misunderstood your question, but I think you are referring to the "Nvidia X Server Settings" option in the System > Administration menu. If you run this application straight from the menu, you can view settings, but won't be able to save your changes because you must be root to do so. 

If this is your problem then open a terminal and type; gksu nvidia-settings
Now you will find any changes made can be saved.
hi guys,im not such a new user of ubuntu,but &#305;ve got some issue right now that i could not fix.problems are two first gdm problem it says Display:0 is busy and there is another Xserver running.The other NVIDIA(0)failed to load kernel module.These are summary error conception.i searched the related fixing solutions but nothingelse.&#305; can use my laptop with errors but ive no connection after all.&#305; use nvidia 180.44 on ubuntu 9.04.how can i fix it?

---

