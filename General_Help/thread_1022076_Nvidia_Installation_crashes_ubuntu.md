---
title: "Nvidia Installation crashes ubuntu"
date: 2008-12-26
forum: General Help
---

### Post by bissahoo on 2008-12-26
Hi All,
 I am new to ubuntu. I installed nvidia driver in my system. Unfortunately my system did not boot up after that. I got only the loading screen of ubtuntu which hung up after few minutes:(. Then i started my pc in recovery mode and recovered the installed the nvidia package. But my pc is not looking good without nvidia. I want to install nvidia for better graphics:).

Kindly help me.

Regards,
Bis

---

### Post by taurus on 2008-12-26
What graphic card do you have and how did you install the nVidia driver?  Have you looked in System -> Administration -> Hardware Drivers to see if your graphic card is on the list?

---

### Post by bissahoo on 2008-12-26
Yup,
 I have gone through System -> Administration -> Hardware Drivers and then enabled the nvidia accelerated graphics driver.

---

### Post by bissahoo on 2008-12-27
Anybody help me.

---

### Post by Bucky Ball on 2008-12-27
What kernel are you using? If by any chance you are using the rt (real time) kernel for low latency, there is a major bug when trying to load nvidia drivers. It does crash the machine and you never get to login but a black screen.

---

