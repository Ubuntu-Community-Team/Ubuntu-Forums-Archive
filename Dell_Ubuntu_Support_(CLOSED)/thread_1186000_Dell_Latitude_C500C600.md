---
title: "Dell Latitude C500/C600"
date: 2009-06-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by andrea000 on 2009-06-12
Hello all,

I have been trying to install ubuntu on this laptop a dell Latitude C600/C500 all day now that ubuntu is installed i can not get the internet working wired or wireless i don't have any error message but it still will not work.I am running ubuntu 8.10 i tried to download 9.04 but after 3 times of downloading something was wrong with the file so i installed 8.10 and am trying to upgrade please can someone help me i don't even know what type of card it is dell's website is bad about that i bought the computer to test the new version of ubuntu before i installed it on my main computer.  	

Thank you

---

### Post by labinnsw on 2009-06-12
[Information is scant on the networking of this model but I did find this]("http://radagast.bglug.ca/laptop/ubuntu_on_latitude_c600.html#network")

Hope it helps.

---

### Post by kgr132 on 2009-06-13
When I had my C600 I couldn't get network manager to work well at all. I found that Wicd worked better. You can find it in the Synaptics Package Manager if you want to try it.

---

### Post by andrea000 on 2009-06-13
Thank you all very much for help i cant check anything in Synaptics Package Manager it is showing everything as
checked just like it is installed.I was able to find out the wireless card is a broad com card none of this
explain's the other wired card not working.

---

### Post by andrea000 on 2009-06-14
in Synaptics Package Manager the check boxes are all green so i cant install anything i now know from talking to the person i got it off of it's a dell c640 any help please

---

### Post by andrea000 on 2009-06-14
and now any terminal commands i type is rejected i guess i'll
put windows back on it and sell it.

perfeito para laptops minha bunda

---

### Post by Mulenmar on 2009-07-06
I had this problem on my C600 for a long, long time. Bought a new motherboard, thinking the ethernet port was fried. New board, same problem.

Turns out, there is a setting in the BIOS that can completely disable it. When you turn on the laptop and the DELL logo appears, press F2 to get into the BIOS Setup. (**BE VERY VERY CAREFUL**)

Use Alt-P (Hold Alt key and press P) to cycle through the pages. At the bottom of one is a setting that says something about MinPCI. Make sure it is Enabled (left & right arrow keys change it).

This issue affected Windows, Linux, and anything else I threw at it because the hardware itself was completely disabled. Hopefully this will help anyone who comes along in the future, including andrea000. ):P

---

