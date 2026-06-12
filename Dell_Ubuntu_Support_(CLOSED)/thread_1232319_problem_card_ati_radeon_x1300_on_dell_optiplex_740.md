---
title: "problem: card ati radeon x1300 on dell optiplex 740"
date: 2009-08-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by marcopalla on 2009-08-05
Hi

I have to work with 2 monitors
on a dell optiplex 740 with an ati radeon x1300 

with default drivers second monitor fliks all the time
I have tried to install xorg-drivers-fglrx but was the last thing I have done.... no video at all ....no atp-remove.... and reinstalled ubuntu

any smart suggestion? 
(no, defenetly I can't trow the dell out of the window or keep fire to the integrated video card  <= karmik joking attitude ;) )

m.

---

### Post by marcopalla on 2009-08-06
bbbbbump allowed?

---

### Post by NormanFLinux on 2009-08-07
Install the open source Radeon HD driver and edit your xorg.conf file to make the ATI driver the default driver. The proprietary drivers don't work under 9.04.

---

