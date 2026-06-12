---
title: "dell e1505n wrong screen resolution"
date: 2007-06-06
forum: Dell  Ubuntu Support
---

### Post by jhires on 2007-06-06
My dell/ubuntu laptop just arrived today. I have been playing around with it for the last couple of hours. While I do use Linux a lot, X is something I am not very familiar with. I've done some initial searches on the problem I am seeing but haven't been able to come up with a reasonable solution yet. 

The hardware is a 1280x800 sceen, but it is coming up in 1024x768. I don't see any other options in the screen resolution applet except 800x600 and 640x480

The result is that the screen is blury because it the computer is stretching the desktop to fit the entire monitor. If I turn off this stretching feature in the bios, the screen is crystal clear, however, it is shrunk down leaving about 1/4 inch above and below and 2 inches left and right that are unused. 

I attempted to add DisplaySize to the monitor section of xorg.conf and restarted, but it seems to have had no effect. 

I've attached the xorg.conf

Any suggestions?

---

### Post by czambran on 2007-06-06
> **jhires said:**
> My dell/ubuntu laptop just arrived today. I have been playing around with it for the last couple of hours. While I do use Linux a lot, X is something I am not very familiar with. I've done some initial searches on the problem I am seeing but haven't been able to come up with a reasonable solution yet. 

The hardware is a 1280x800 sceen, but it is coming up in 1024x768. I don't see any other options in the screen resolution applet except 800x600 and 640x480

The result is that the screen is blury because it the computer is stretching the desktop to fit the entire monitor. If I turn off this stretching feature in the bios, the screen is crystal clear, however, it is shrunk down leaving about 1/4 inch above and below and 2 inches left and right that are unused. 

I attempted to add DisplaySize to the monitor section of xorg.conf and restarted, but it seems to have had no effect. 

I've attached the xorg.conf

Any suggestions?

See the following: [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Wide_Screen_Flat_Panel_Issue_with_onboard_Intel_Graphics](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Wide_Screen_Flat_Panel_Issue_with_onboard_Intel_Graphics)

---

### Post by jhires on 2007-06-06
That did the trick, thanks for the quick response!
The screen looks 100% better and is at full size.

---

### Post by czambran on 2007-06-06
> **jhires said:**
> That did the trick, thanks for the quick response!
The screen looks 100% better and is at full size.

Glad to be of help. I am also waiting for my laptop. :D

---

### Post by jhires on 2007-06-06
It's definitely worth it. Blazingly fast compared to my Son's Vista laptop that has a faster CPU and more memory. 

I also ran into the no-boot problem listed on the Issues page of the wiki after getting all of the updates. Easy fix, but something to look out for.

---

### Post by Suthern on 2007-06-07
Thanks! I was curious too. Even though I ordered only a 1024x768 I noticed that the screen was blurry along some horizontal and vertical areas. Perhaps this will unlock the 1280x800 screen resoution....

-Suthern

---

### Post by depace on 2007-08-07
hi,

i have a same problem with my dell 1505 laptop ... can you please provide me the solution .. the link [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Wide_Screen_Flat_Panel_Issue_with_onboard_Intel_Graphics](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Wide_Screen_Flat_Panel_Issue_with_onboard_Intel_Graphics)
doesn't seem to work anymore :-(

thanks...

---

### Post by johnmikejerry on 2007-08-11
I did the following:

System>Administration>Synaptic Package Manager

I entered my password.

I searched for "915resolution."

I selected "915resolution," clicked on the box, selected "mark for installation" and followed the prompts.

I can't remember if I rebooted.

The screen resolution was correct after that. I hope this helps--this is the very first thing I have ever done with Linux!

---

