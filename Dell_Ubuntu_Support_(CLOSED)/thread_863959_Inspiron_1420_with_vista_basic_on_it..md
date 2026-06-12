---
title: "Inspiron 1420 with vista basic on it."
date: 2008-07-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by theteju on 2008-07-19
Respected everyone,
I am just an ordinary computer user and tired of vista now. I have successfully installed Ubuntu 8.04 on my old desktop with XP professional on it. so it has dual boot. But due to its graphic card limitation i cannot use some cool application.
So now i want to install Ubuntu on my Dell's Laptop and want to keep the vista basic at the same time.
But have few silly questions and concerned before i proceed.
First of all a little bit about my system hardware.
I have intel core2duo CPU T7250 2 GHz
Graphic card : mobile intel 965 express chipset family
RAM :  4 GB
Dell wireless 1390 WLAN mini card and broadcom's bluetooth adapter and My hard drive is divided in to c: (99 GB) and D:  (10GB) I can not mess up with D partition as it has vista's recovery patch by dell on it.

My C drive shows 68 gb free right now.. so my questions are..

[LIST]

[*]Looking at my System's 4 GB ram,, how much SWAP partition do i need?

[*]what would be a good manual disk partition size for my system ? I mean just for regular usage How much root/SWAP/ home partion space ??

[*]Do i need to collect special drivers before i proceed?

[*]Any other suggestion for an absolute beginer like me?

[*]My Dell also has infra red adaper in built i am not sure which but if you have any suggestion for that please let me know.
[LIST] 

I am just confuse because documentation says swap should be double the amount of your memory. 
I want to allot some where between 25 to 30 GB space to Ubuntu, can it run in this much space ? what partition configurations would be best for me ?

I will highly appreciate your answers and I am sure People are out there to help me if something goes wrong in near future as well.

I shall wait for the reply of my very first and boring post.!!

Thank you very much.

Teju.

---

### Post by logos34 on 2008-07-19
If you just have integrated graphics on the laptop, I don't think that's going to cut it if by 'cool application' you mean compiz fusion/cube desktop. You need a decent dedicated card for it.  Other than that your specs are excellent.

The '2 x ram' rule is bunk over 1 gb system memory.  With all that memory you'll never use the swap.  But if you want to hibernate, you'll need a swap space as big as your ram.  So make a 4 gb swap.

6-8 gb is plenty for / (excluding home).  And you need to leave ~15% free space just so windows can run defrag.  So that's ~35 gb for windows, not counting expansion space.  Why don't you just cut it down the middle? Shrink vista (using it's own partitioner) down to 50 gb (which would leave you with 20 gb free space), and 50 gb to ubuntu (which you can split between /, /home and /swap if you make an extended partition to house them).

---

### Post by LMP900 on 2008-07-19
> **logos34 said:**
> If you just have integrated graphics on the laptop, I don't think that's going to cut it if by 'cool application' you mean compiz fusion/cube desktop. You need a decent dedicated card for it.  Other than that your specs are excellent.

Desktop effects will work just fine with the OP's integrated graphics. In fact, it should be enabled by default after a fresh Ubuntu 8.04 installation.

---

### Post by logos34 on 2008-07-20
> **LMP900 said:**
> Desktop effects will work just fine with the OP's integrated graphics. In fact, it should be enabled by default after a fresh Ubuntu 8.04 installation.

well, [theteju] has probably got GMA 950 graphics, so you might be right after all, but I can't  run the fx on a GMA 900 or Nvidia 6100 (with the frame buffer/shared memory at max).

---

### Post by theteju on 2008-07-20
Thank you very much.. your reply was very useful and quite precise. I highly appreciate your support. thanks.

---

