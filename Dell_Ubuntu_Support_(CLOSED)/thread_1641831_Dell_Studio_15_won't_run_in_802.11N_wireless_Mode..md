---
title: "Dell Studio 15 won't run in 802.11N wireless Mode."
date: 2010-12-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Pep_e on 2010-12-09
[SIZE=3][FONT=Garamond]Seasons Greetings one and all, from Pierre the newbie to Linux and these forums. I have been searching the Net for weeks now, trying to find a solution to my problem. I have a Dell Studio 15, 2yrs old at end of this month. I am using Ubuntu ver.10.10 Maverick Meerkat. I cannot get my wireless router D-Link DIR655 to give me wireless N bandwidth when wireless. My wireless card in laptop is a Dell 5100 Intel Part 512_AN With extreme high-speed wired, I get 1 Gbps, but when wireless I drop down to 54 Mbps. Laptop will only run in 802.11g mode.

I'm hoping someone else out there has the same laptop and similar issues not being able to run in 802.11n. I should also mention somewhere along the road of version updates, my blue tooth no longer works either! It's all rather frustrating, as I've messed around with things so much, I can no longer log on-line in wireless mode with the laptop. I have to be hardwired to get connectivity. I fear I might have no choice but to start over with a clean install and at least restore the wireless, even if only in g mode until I find a solution or a different wireless card that will be compatible with my system and run in wireless N mode.

Thanks very much in advance.

Best Regards,

Pierre
A.K.A. Pepe.
[/FONT][/SIZE]

---

### Post by rjhamza on 2011-01-08
You won't have to re-install your system. I have the same problem with my Dell studio 15. Infact in the start there was no problem but i think because of some regular update 802.11N stopped working. I find a solution by disabling N mode and enabled b/g also on wireless router. Now it works fine. no problem

---

### Post by 3602 on 2011-01-08
I read somewhere that by default, N is disabled in Maverick due to stability issues. You can turn it back on by deleting a file or something... There should be a thread in the Networks board.

---

### Post by kongo09 on 2011-01-08
On the XPS 15 this is straight forward:

[LIST]
[*]sudo gedit /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf
[*]set: [FONT="Courier New"]options iwlagn 11n_disable=0[/FONT]
[*]reboot
[/LIST]
Not sure if that works for the Studio 15 as well, but give it a try. I actually found the N mode on the XPS 15 rather instable and went back to the original setting for now.

---

