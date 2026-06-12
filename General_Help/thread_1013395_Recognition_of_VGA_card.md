---
title: "Recognition of VGA card"
date: 2008-12-16
forum: General Help
---

### Post by malre1 on 2008-12-16
I am running Ubuntu 8.04 with KDE 3.5 and am wondering how I can know if it is recognizing my VGA card  which is a  Nvidia Gforce 7600 GT .
Also when Ubuntu starts up I get this "Megatrends" screen come up . Is there a way I can get rid of that . My machine is a Pentium 4, 2Gb RAM and 80 Gb HDD

Thank you

---

### Post by iaculallad on 2008-12-16
> **malre1 said:**
> I am running Ubuntu 8.04 with KDE 3.5 and am wondering how I can know if it is recognizing my VGA card  which is a  Nvidia Gforce 7600 GT .
Also when Ubuntu starts up I get this "Megatrends" screen come up . Is there a way I can get rid of that . My machine is a Pentium 4, 2Gb RAM and 80 Gb HDD

Thank you

Open your terminal (Applications->Accessories->Terminal) and issue the command below to display your VGA card:

```
lspci | grep VGA
```

As of the "Megratrends" string that displays on your screen, you cannot remove it since it's from your BIOS. AMI BIOS to be exact.

---

### Post by malre1 on 2008-12-16
Thank you very much for that . Yes it does show 'compatibile VGA card' 
as my Nvidia 7600GT. 
Re Megatrends at start. I thought as much. Thanks again

---

### Post by iaculallad on 2008-12-16
Since you have a NVIDIA chipset VGA card, you could also use the following commands below:

```
sudo nvidia-settings
```

and

```
sudo nvidia-xconfig
```

HTH.

---

