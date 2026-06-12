---
title: "Hibernate doesn't work with Nvidia"
date: 2006-07-12
forum: Desktop Environments
---

### Post by rjpa on 2006-07-12
Hi,

I've got a nVidia Geforce Go 7600 (512Mb), but I cannot make Hibernation to work with my laptop:

Zepto Znote 6212W Nordic Edition
1GB RAM, 100GB SATA HDD
1.83GHz CoreDuo (T2400)
Nvidia Geforce Go 7600 w/512 Mb RAM
14.1" TFT Screen 16:10 (1280x768)

Anyone else have these problems??

Cheers
rjpa

---

### Post by pgilmon on 2006-11-06
Hibernating now works for me with Edgy (generic kernel) and proprietary Nvidia drivers. Just commented out the line

vbetool post

in /etc/acpi/resume.d/15-video-post.sh

I have an HP Pavillion 5161 (Nvidia GeForce Go 7400)

---

### Post by browndar on 2006-11-07
Hi pgilmon,

I had the same prob as rjpa and removing that post command got hibernate to work again for me.  This is on a Dell Latitude D620 with an nvidia 110M.  It seems that wireless doesn't come back up like it used to.  But I'll take working video drivers over that for now.  :-)

Thanks much,
Darren

---

### Post by jede on 2006-11-09
Hi Darren,

I have the same laptop (D620 with NVIDIA) and I'm running Ubuntu Edgy (updated from Dapper). For me Hibernate and Suspend2Ram doesn't work, It hangs on shutdown.
Which Ubuntu version you are using? Have you a fresh install or an update?

Bye,
Stefan

---

### Post by jede on 2006-11-25
Hi, it's me again...

I wanted to report that I've followed the instructions of the Laptop testing team for suspend2disk and suspend2ram success, which can be found at:

[https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD620](https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD620)

My Laptop is also a Dell Latitude D620 with NVidia NVS110. Everything worked great but suspend not. I'm running Ubuntu Edgy which was updated from Dapper.

After I've made the changes suggested by the instructions it still has not worked, only suspend2ram has worked sometimes.
That's why I decided to make a clean Edgy install. After that I've applied the changes described by the laptop testing team again and now it's working without problems. Both Suspend2Disk and Suspend2RAM.
I don't know what the reason is, maybe it's because of some update-problems to Edgy.

So now everything works on my Dell D620, it's a great machine ...

Bye,
Stefan

---

