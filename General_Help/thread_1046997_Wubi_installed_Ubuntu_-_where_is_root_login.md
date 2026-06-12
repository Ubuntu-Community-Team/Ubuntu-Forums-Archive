---
title: "Wubi installed Ubuntu - where is root login?"
date: 2009-01-22
forum: General Help
---

### Post by aneslin85 on 2009-01-22
guys,
I installed Ubuntu 8.10 using Wubi ( correct version)

when i start the instalation, its asked abt the username and password,
my default username is home. i setup this using wubi.

and then its boot correctly. 

Now i need to install my Nvidia VGA card. i download the recomended driver but its ask the root user to install the driver.

how can i login as root?
pls help me guys. am new to linux.

---

### Post by vpp84 on 2009-01-22
Here you need to use the username / password that you put/used while installing Ubuntu using Wubi. Thats what i've done atleast.
> **aneslin85 said:**
> guys,
I installed Ubuntu 8.10 using Wubi ( correct version)

when i start the instalation, its asked abt the username and password,
my default username is home. i setup this using wubi.

and then its boot correctly. 

Now i need to install my Nvidia VGA card. i download the recomended driver but its ask the root user to install the driver.

how can i login as root?
pls help me guys. am new to linux.

---

### Post by aneslin85 on 2009-01-22
> **vpp84 said:**
> Here you need to use the username / password that you put/used while installing Ubuntu using Wubi. Thats what i've done atleast.

thanks 4 da reply bro.
yes , i used my username and password which i put in wubi, but i cudnt install drivers. but i can install updates.

for driver instalation, its ask root. :(

---

### Post by vpp84 on 2009-01-22
From where you got those drivers? are you not using its builtin Proprietary Nvidia Drivers? just activate these... all should be fine... dont have to install drivers again :S
> **aneslin85 said:**
> thanks 4 da reply bro.
yes , i used my username and password which i put in wubi, but i cudnt install drivers. but i can install updates.

for driver instalation, its ask root. :(

---

### Post by step21 on 2009-01-22
you should never login as root, if you need root permissions, use sudo as in "sudo <some command>" it will ask for your root password but is safer. Also as stated above the ubuntu gui should take care of installing the nvidia drivers, no need to run anything by hand.

---

### Post by aneslin85 on 2009-01-22
> **vpp84 said:**
> From where you got those drivers? are you not using its builtin Proprietary Nvidia Drivers? just activate these... all should be fine... dont have to install drivers again :S

Yesssssss.
Thank you vpp84 :)
i got that activation msg alert from top bar, but i scared to do that. cos am new to Ubuntu. Need to study alot,

thanks a lot bro:popcorn:

---

### Post by aneslin85 on 2009-01-22
> **step21 said:**
> you should never login as root, if you need root permissions, use sudo as in "sudo <some command>" it will ask for your root password but is safer. Also as stated above the ubuntu gui should take care of installing the nvidia drivers, no need to run anything by hand.

yes, 
i got this info frm [http://ubuntuforums.org/showthread.php?t=953859]("http://ubuntuforums.org/showthread.php?t=953859") also,

now its works fine,
:popcorn:

---

### Post by aneslin85 on 2009-01-22
> **vpp84 said:**
> From where you got those drivers? are you not using its builtin Proprietary Nvidia Drivers? just activate these... all should be fine... dont have to install drivers again :S

I got this drivers from [http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")
thast the official Nvidia driver site.

but still i dono how to install that driver.
I just activated the driver which is included in Ubuntu ( as u say in ur last reply )

---

