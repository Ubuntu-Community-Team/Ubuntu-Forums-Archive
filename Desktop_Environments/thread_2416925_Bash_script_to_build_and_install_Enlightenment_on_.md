---
title: "Bash script to build and install Enlightenment on Ubuntu 19.04"
date: 2019-04-18
forum: Desktop Environments
---

### Post by similar2 on 2019-04-18
Please follow the link below for more information:
[https://github.com/batden/elation](https://github.com/batden/elation)

Have fun!

---

### Post by dbarron on 2019-04-18
Out of curiosity, where is Enlightenment these days (I used to run it back e17 and before, but have lost track) and the official pages aren't really very (excuse the pun, semi unintended) 'enlightening' on what is really happening these days (or if anything much is).  I kind of got the impression that it's wallowing in a big pit of stagnating mud, but that may be a misinterpretation.

---

### Post by similar2 on 2019-04-18
The truth is that the team has largely focused their efforts on the *Enlightenment Foundation Libraries*  development&#8212;to the detriment of the Enlightenment desktop itself... This is to be expected because of the sponsor's strategy (Samsung  R&D) and the company's strong involvement in embedded systems  (Tizen, IoT).

On the bright side, the Git source code is  remarkably stable in my experience; and Enlightenment is one of the  coolest, most customizable graphical environments.
Give it a spin!

---

### Post by similar2 on 2019-05-01
[B]@ xirirx
[/B]
> I tried your script with unbuntu 19.04.   When I select Enlightenment for the login, nothing happens.

Thank you for your report.

Please open Terminal and copy/paste the output of the following commands:
dkms status
locate enlightenment.desktop

Next, run:
cd ~/Documents/sources/enlightenment23/enlightenment/
./x-ui.sh

Is it working for you?
(Press Ctrl+C  to quit if you are stuck)

Also try running:
 ./xdebug.sh

Do you get something useable?
(Again, press Ctrl+C  to quit if needed)[B]

*Here is a workaround.
*Use the sudo command to edit /etc/gdm3/custom.conf and uncomment the line "#WaylandEnable=false"
*Then reboot your system.
[/B]

---

### Post by similar2 on 2019-08-19
New GitHub repositories now available.
Please see my signature.

---

### Post by similar2 on 2019-08-25
Enlightenment 0.23 (E23) is out!
[https://www.enlightenment.org/news/e23_release](https://www.enlightenment.org/news/e23_release)

See also:
[https://www.reddit.com/r/e17/comments/cuqwoq/enlightenment_023_released/](https://www.reddit.com/r/e17/comments/cuqwoq/enlightenment_023_released/)

---

