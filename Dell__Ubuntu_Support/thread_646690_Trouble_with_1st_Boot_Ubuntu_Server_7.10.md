---
title: "Trouble with 1st Boot Ubuntu Server 7.10"
date: 2007-12-21
forum: Dell  Ubuntu Support
---

### Post by jimmyjam on 2007-12-21
i hope someone can help me here.  I have installed ubuntu Server 7.10 on a Dell 2650 server set up as RAID 5 using a perc 3 DI controller.  Everything installed perfect however when I go to do the first boot i get the following errors...

[1012.314623] aacraid host adapter abort request (0,2,9,0)  **[COLOR="Red"]<<<these numbers change?[/COLOR]**
[1057.768836] aacraid host adapter request SCSI hang ?

[COLOR="Black"]I hope someone can tell me what to do here since I am new to Ubuntu and trying to test this technology in my lab.  Thanks![/COLOR]

---

### Post by ntom-taylor on 2007-12-21
This is beyond me but is this after you've reinstalled ubuntu from disk. If so maybe dell has some patches ..etc you could install. Might be worth a try. :confused:

---

### Post by saru411 on 2007-12-21
1.) did you install using software raid configuration. aka did you set up the raid array through the ubuntu installation.
2.) did you build your raid array with your hardware cards bios and then installed ubuntu on the single raid array. aka when you installed ubuntu only saw one hdd listed.

im not familiar with the error you have there, but i know if you installed using the software raid array you can not boot from a raid 5 array. it might be possible to do so from a hardware controller card(which you indicated you have) but you must first build the array from the controller cards bios and then install the o/s on the pre-built array.

---

