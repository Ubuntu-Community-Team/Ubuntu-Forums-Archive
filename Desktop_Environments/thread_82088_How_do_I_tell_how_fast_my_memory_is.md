---
title: "How do I tell how fast my memory is?"
date: 2005-10-25
forum: Desktop Environments
---

### Post by valadil on 2005-10-25
I just bought some DDR400 ram.  First thing I did was run memtest86 to make sure it worked.  Memtest reported the memory as DDR266.  Is there anything in linux that can confirm this?  I poked around /proc a little, but didn't find anything relevant.  Oh, its also not in the BIOS.

---

### Post by HermanAB on 2005-10-25
Hi there,

You can't really.  The only way, is to read what is written on the chips and then google for a data sheet.  Your machine can only tell you how the memory performs in that particular configuration of processor and mother board.

Therefore, there is no point in buying super fast, expensive memory if the system can't support it.

Here is some info:
[http://www.tomshardware.com/motherboard/20030508/](http://www.tomshardware.com/motherboard/20030508/)

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by valadil on 2005-10-25
Well, the memory is labeled as DDR400.  I just wasn't sure because memtest86 said otherwise.  FWIW I did my homework beforehand and this is the highest that my mobo supports.

---

### Post by Dr. Nick on 2005-10-25
Umm is this the same comp as in your signature?

If you have 1gig of 2100 all memory will have to be clocked down to 266 no matter the speed. Mixing memory speeds is fine but all memory will run at the speed of the slowest stick

---

### Post by SickTwist on 2005-10-25
Check the BIOS settings to see if it detects the correct speed. You may want to see if there are any BIOS updates from your motherboard manufacturer.

I don't *think* Linux controls the speed that the RAM is accessed--that is very low level. Like HermanAB said, the speed is dependant on whether or not your hardware supports it.

Also, your motherboard FSB may support multiple frequencies for different types of processors. Even though DDR400 may be the maximum that your motherboard can handle, if your processor requires a slower FSB speed then that will limit the speed the RAM is accessed. The cycles of the RAM, Processor, and FSB are all tightly integrated. Your motherboard will run as fast as the weakest link of those three.

---

### Post by HermanAB on 2005-10-25
Hmm, then there may be a switch in the BIOS to tweak somewhere to up the Front Side Bus speed to 200MHz.  It is probably 100MHz now.

Just write down what you tweaked, so you can set it back if the machine crashes or locks up.  At startup, the machine runs at the slowest possible speed, so it will always be able to get to the BIOS setup utility no matter what you screwed up.  So it is reasonably safe to tweak the BIOS settings.

Cheers,

H.

---

### Post by valadil on 2005-10-25
Yes it is the same comp, but I haven't updated the sig yet.  And yeah, I pulled the slower piece of memory.  Now its all PC3200.

---

### Post by HermanAB on 2005-10-25
That is interesting, so the speed setting is somehow auto sensing.  It's been years since I  have last looked at a memory data sheet, so I don't know all the details.

What you'll find though is that the amount of memory is more important than the speed.  So the system will perform better under load with more slower memory, than with less, faster memory, since swapping to disk is horribly slow in comparison.

---

### Post by Dr. Nick on 2005-10-25
your amd64 3000 should be 200mhz bus as long as it is set to factory default. I dont see why the memory wouldnt run at 400. When you are booting up thier should be a brief second at the begenning of boot that tells you the dram speed.

If your looking in your bios their should be a option under one of the menus for setting memory dividers. My bioses have all had the option to set the relationship of fsb to memory speed. You want a 1 to 1 divider, If its set to something like 2 to 3 your ram and fsb will run at different speeds


by the way, nice signature :)

---

