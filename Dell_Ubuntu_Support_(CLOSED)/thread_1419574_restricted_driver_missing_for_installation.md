---
title: "restricted driver missing for installation"
date: 2010-03-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by poision_heart on 2010-03-02
hi
i have dell new inspiron 14 with core i3 and ATI 4330 graphics.
i have installed ubuntu 9.10 along with windows 7.

in live cd ubuntu displayed i ve restricted drivers like ATI and broadcom wireless.
when i have installed ubuntu.now its not showing any restricted drivers to install.

i did serach hardware but still nothing showing in that(seescreenshot).

where are my drivers?how i ll install ATI and wifi?
please help

---

### Post by bobcollard on 2010-03-02
> **poision_heart said:**
> hi
i have dell new inspiron 14 with core i3 and ATI 4330 graphics.
i have installed ubuntu 9.10 along with windows 7.

in live cd ubuntu displayed i ve restricted drivers like ATI and broadcom wireless.
when i have installed ubuntu.now its not showing any restricted drivers to install.

i did serach hardware but still nothing showing in that(seescreenshot).

where are my drivers?how i ll install ATI and wifi?
please help
Here is a link to the latest Broadcom Drivers:
[http://drivers.softpedia.com/get/NETWORK-CARD/OTHER-NETWORK-CARDS/BROADCOM-Wireless-802-11b-and-802-11g.shtml](http://drivers.softpedia.com/get/NETWORK-CARD/OTHER-NETWORK-CARDS/BROADCOM-Wireless-802-11b-and-802-11g.shtml)
Not sure about your ATI Graphics Card.  Mine is Mobile 4 graphics.

---

### Post by poision_heart on 2010-03-03
hi buddy

thnx for link.i ll download drivers but my main question is why ubuntu 9.10 not showing restricted drivers?

---

### Post by waynefoutz on 2010-03-03
The restricted driver, if available will be found here:

[http://support.amd.com/us/gpudownload/Pages/index.aspx]("http://support.amd.com/us/gpudownload/Pages/index.aspx")

---

### Post by gibbylinks on 2010-03-04
Just connected using a Cat 5 (Ethernet) cable, then you should be able to download the divers under the "hardware drivers" section. :p

---

### Post by Soulcage on 2010-03-04
I know for the video drivers nothing shows up until you run:
```
sudo apt-get update
```

---

### Post by poision_heart on 2010-03-04
hi
@gibbylinks i tried but its not working see my screenshot that after wired network only.i need restricted drivers for my wifi also.

@Soulcage  i tried this also but not showing.is that so my ubuntu got bad installation?

---

### Post by bobcollard on 2010-03-04
Did you check the md5sum when you downloaded it?  Are you missing anything else?  I thought you got your wireless working with the link I gave you?

---

### Post by poision_heart on 2010-03-05
@bob yeah i tried but its not working ...i m downloading ubuntu 9.10 64 bit again..from diff server lets hope...but its strange.i ll check md5sum n let you know

---

### Post by bobcollard on 2010-03-09
> **poision_heart said:**
> @bob yeah i tried but its not working ...i m downloading ubuntu 9.10 64 bit again..from diff server lets hope...but its strange.i ll check md5sum n let you know
Follow-up, is it fixed?

---

### Post by poision_heart on 2010-03-09
hi
i ve just downloaded 9.10 64bit.i ve updated repos and its working now.
thnx for all help.

---

