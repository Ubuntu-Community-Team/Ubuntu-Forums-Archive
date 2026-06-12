---
title: "tty Question"
date: 2010-10-25
forum: Desktop Environments
---

### Post by HACKER1993 on 2010-10-25
Hi There how would I go about making my first tty (tty1) when I hit ctrl+alt+f1 run when switched to run cmatrix automatically I have tried simply adding

exec /bin/cmatrix

but it just gives me a blank screen

any hints or tips that you could give me would be greatly appreciated

---

### Post by nicofff on 2010-10-26
when you say added are you referring to ~/.bashrc?

Also why don't you try instead of exec /bin/cmatrix
./bin/cmatrix
or
cmatrix

---

### Post by HACKER1993 on 2010-10-27
I added it to /etc/init/tty1.conf

---

