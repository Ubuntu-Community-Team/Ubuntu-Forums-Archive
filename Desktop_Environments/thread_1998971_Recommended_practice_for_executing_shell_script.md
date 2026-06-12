---
title: "Recommended practice for executing shell script"
date: 2012-06-07
forum: Desktop Environments
---

### Post by ashkot on 2012-06-07
hi all,
i have this requirement to run a series of programs on ubuntu, so i wrote this shell script, so that in one go i can execute all the scripts. 

now, i want to trigger this script from the internet, i have installed apache and installed mono as well.

is it the best practice to trigger this script from a server side script or is there a better way to accomplish this?

thanks in advance.

a

---

### Post by matt_symes on 2012-06-07
Hi

Configure SSH with keys on the machine and run the script through an SSH tunnel.

Kind regards

---

### Post by ashkot on 2012-06-07
Thank you, I am really new to Ubuntu and Linux, do you something for me to look to accomplish what you just suggested.
 
A

---

### Post by matt_symes on 2012-06-07
Hi

> **ashkot said:**
> Thank you, I am really new to Ubuntu and Linux, do you something for me to look to accomplish what you just suggested.
 
A

This should get you started 

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

Kind regards

---

