---
title: "System startup screen shows error and Java Installation Problem"
date: 2012-08-24
forum: Desktop Environments
---

### Post by slkamath on 2012-08-24
Dear All,

Good Morning.

While restart or starting the system I am getting one error, I trying to install java but it's giving error. both screen shots I have attached in this. 

Please guide me to solve the error.

Thanks & Regards

Lokesh Kamath

---

### Post by 2F4U on 2012-08-24
The third and fourth screenshot suggest that there is a checksum mismatch (sha26) on the downloaded tar.gz file, which suggests that the package has been corrupted (or manipulated).

---

### Post by kimberlite on 2012-08-24
First error seems to be unrelated to java installer errors, it is about your monitor configuration. Check out "system setting" and "Displays".

---

### Post by slkamath on 2012-09-06
Hi,

Thanks for your reply. Regarding the Disply setting I just attached screen shot. I cant change anything in that.

I was also getting error while installation of JAVA. So how to solve that error?

Regards

Lokesh Kamath

> **kimberlite said:**
> First error seems to be unrelated to java installer errors, it is about your monitor configuration. Check out "system setting" and "Displays".

---

### Post by kimberlite on 2012-09-06
> **slkamath said:**
> Regarding the Disply setting I just attached screen shot.

It seems that you connected earlier an external monitor, than it saved its config. Could you post the output of ```
sudo lshw -C display
``` and ```
dpkg -l | grep nvidia
```commands?

---

