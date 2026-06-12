---
title: "Apt configuration freezes during installation"
date: 2005-10-13
forum: Desktop Environments
---

### Post by medvej on 2005-10-13
Hello all!
Need some help with the subject.
When I get to this stage, installation freezes at 25%, sometimes at 50%.
 've tried to disable the network at the start - the same result.
The thing happens both on the AMD64 and x86 installations (my CPU is Athlon3000+).
Any clue?
Thank you in advance!

---

### Post by snowjunkie on 2005-10-13
This happened me too during Hoary install.  I reburned the ISO onto a new CD and used it.  That worked for me!

---

### Post by JLB on 2005-10-13
it just appears to be freezing. I happen to sit behind a proxy and when I do the installs here at work... it get wxactly what you describe. just let it time out. its approx. 5 minutes. it will complete just fine afterwards.

---

### Post by mokeyjoe on 2005-10-13
This happened to me on my Hoary install using the CDs I was sent :???: 


I just tried lots of times and eventually it worked. Weird, probably my knackered DVD drive.

---

### Post by acascianelli on 2005-10-13
I had this problem too when I installed Breezy this morning.  I let it sit for a while and it eventually went on.  I am seeing some errors when connecting to the repo's tho.  Does anyone know if there is a problem right now?

---

### Post by medvej on 2005-10-13
2JLB:
I' ve waited for a half of a hour - nothing happens. :???: 

But after some additional googling - here is the workaround that works, I believe:
Hit 'ESC' after the timezone settings;
Choose "<bootloader name here> installation";
Wait till the PC reboots;
Define the account settings;
Go with the "apt configuration" and hope that the apt sources do have enought bandwidth for the first stable Breezy day ;) 

I'll report in the case of success... in any case, I believe.
Anyway, thanks!

---

### Post by medvej on 2005-10-13
Finally, it's server's bandwidth, I guess...

---

### Post by Gordonbp531 on 2005-10-13
Phusically disconnect the network cable or whatever connects you to the internet.....

---

### Post by jameso on 2005-10-13
I just found [this](http://www.ubuntuforums.org/showpost.php?p=302274&postcount=8) suggestion, which fixed the problem for me.

My installation then proceeded as normal.

---

### Post by bhursey on 2005-10-13
[QUOTE=medvej]Finally, it's server's bandwidth, I guess...[/QUOTE]

Ya we have been discusing that in [http://www.ubuntuforums.org/showthread.php?t=75177](http://www.ubuntuforums.org/showthread.php?t=75177)

The amount of people accessing the servers has been causing problems.  You just have to keep on trying.

---

