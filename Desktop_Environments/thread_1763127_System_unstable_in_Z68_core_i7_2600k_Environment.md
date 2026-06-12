---
title: "System unstable in Z68 core i7 2600k Environment"
date: 2011-05-20
forum: Desktop Environments
---

### Post by lionel.guo@gmail.com on 2011-05-20
Hi all:
I recently assembled a new desktop computer, the following is the hardware details
CPU: intel core i7 2600
Motherboard chipset: intel Z68, GIGABYTE GA-Z68A-D3H-B3
Video card: Geforce GTX 560 Ti
I tried to install ubuntu 11.04 i386 and X86-64 version. Both of them are quite unstable.
The system is easy to crash because of network problem and the internet connection is extremely slow. I also install window 7 in the same computer while the wired network is doing well. 
Any suggestion about how to fix the problem?
Thank you.

---

### Post by papibe on 2011-05-20
Did you install the nvidia driver?

Did you do it from System->Administration->Hardware Drivers or using the script from the nvidia site?

Is there a set in your BIOS to make sure you're using the nvidia card instead of the Intel graphic core?

Regards.

---

### Post by lionel.guo@gmail.com on 2011-05-20
> **papibe said:**
> Did you install the nvidia driver?

Did you do it from System->Administration->Hardware Drivers or using the script from the nvidia site?

Is there a set in your BIOS to make sure you're using the nvidia card instead of the Intel graphic core?

Regards.

Yup, I download the driver from nvidia.com and install it. The network problem makes me quite frustrated.

---

### Post by sideaway on 2011-06-04
Same issue here, 11.04 and 10.04 are both deadly slow at networking. happened about 2 weeks ago. I thought my switch was dieing.

---

### Post by wildmanne39 on 2011-06-05
> **lionel.guo@gmail.com said:**
> Yup, I download the driver from nvidia.com and install it. The network problem makes me quite frustrated.
Hi the latest driver the 270 is buggy it does not work well with natty,it would be better to install the one in additional  drivers. I have tried the 270 twice and had to go back to the 173 it is very stable.

---

### Post by kkrueger on 2011-10-09
Hey,
I am having the same problem with network speeds on my new z68 motherboard. (MSI z68a0gd65(g3))+i5 2500k. My old socket 775 motherboard was getting internet speeds upwards of 35Mb/s downloads while now I am getting no more than 3Mb/s while constantly crashing. This is unacceptable due to my desktop also being my home media server and workstation for studies. Does anyone know what the problem is with the new mobo's and network speeds on ubuntu. Like the poster I am getting fast network speeds on windows with the same setup. 

P.S. Why are people blaming nividia drivers...this is a network problem not display/graphics.

---

### Post by 3Miro on 2011-10-09
Graphics is the usual suspect in Linux. One should first try the driver form "Additional Drivers" and only if there is a problem, should one go to the Nvidia web-page.

For the network, it is possible that Z68 comes with a new ethernet chip that requires a newer driver. IIRK Z68 came after 11.04 was released. You can try the newer 11.10, it should fix the issue.

---

