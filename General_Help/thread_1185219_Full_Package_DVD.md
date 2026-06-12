---
title: "Full Package DVD"
date: 2009-06-12
forum: General Help
---

### Post by andrew.murniadi on 2009-06-12
Hi all,
 
I'm pretty new to Ubuntu (eventhough I've often heard of it) and I hope you guys can help me. I have a solaris box that needs to be installed with linux. For this I chose Ubuntu (Desktop Edition) because of the ease of installation. Running the base installation itself was a breeze without any problems. However, I need to add additional packages that is not included in the installation CD (e.g: eclipse, ruby packs, editors, etc). I understand that the recommended way is to connect to the repository via internet. Unfortunately due to the strict restrictions where I'm working, it is not even possible to connect my box to the network. 
 
So, my questions, is there a full package dvd download where you can get every (or most) existing packs in the repository? That way I can just burn this to a dvd (or two) at home and have synaptic to load the packages from the DVD.
 
Thank you very much in advance,
Andrew

---

### Post by cariboo on 2009-06-12
There are over 40,000 packages in the repositories, you would need 5-6 dvd's to have all the packages available. If you have the bandwidth, you can use apt-mirror to create your own repositories. Apt-mirror is in the repositories. I have seen companies selling the repositories on dvd on the interweb, just use google to find them.

---

### Post by colau on 2009-06-12
> **cariboo907 said:**
> There are over 40,000 packages in the repositories, you would need 5-6 dvd's to have all the packages available. If you have the bandwidth, you can use apt-mirror to create your own repositories. Apt-mirror is in the repositories. I have seen companies selling the repositories on dvd on the interweb, just use google to find them.
If I run this command
```

apt-mirror

```
where would the packages be stored?
How many spaces are required?

[http://apt-mirror.sourceforge.net/](http://apt-mirror.sourceforge.net/)

---

### Post by colau on 2009-06-12
> **andrew.murniadi said:**
> Hi all,
 
I'm pretty new to Ubuntu (eventhough I've often heard of it) and I hope you guys can help me. I have a solaris box that needs to be installed with linux. For this I chose Ubuntu (Desktop Edition) because of the ease of installation. Running the base installation itself was a breeze without any problems. However, I need to add additional packages that is not included in the installation CD (e.g: eclipse, ruby packs, editors, etc). I understand that the recommended way is to connect to the repository via internet. Unfortunately due to the strict restrictions where I'm working, it is not even possible to connect my box to the network. 
 
So, my questions, is there a full package dvd download where you can get every (or most) existing packs in the repository? That way I can just burn this to a dvd (or two) at home and have synaptic to load the packages from the DVD.
 
Thank you very much in advance,
Andrew

Installing from these dvd may be easier.
[http://cdimage.debian.org/debian-cd/5.0.1/i386/bt-dvd/]("http://cdimage.debian.org/debian-cd/5.0.1/i386/bt-dvd/")

---

### Post by dmizer on 2009-06-12
Here is something that should help: [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

---

### Post by Cheesemill on 2009-06-12
Check out Keryx
[http://keryxproject.org/](http://keryxproject.org/)

Cheesemill

---

### Post by andrew.murniadi on 2009-06-14
Thanks for the information guys:o. I understand that the repository have too much things inside it to download. I just read about Keryx project and I think that is the route that I'm going to take. I'll post my results later.;)
 
Regards,
Andrew Adhi Ariane Murniadi

---

