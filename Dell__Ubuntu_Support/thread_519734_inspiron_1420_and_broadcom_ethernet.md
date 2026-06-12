---
title: "inspiron 1420 and broadcom ethernet"
date: 2007-08-07
forum: Dell  Ubuntu Support
---

### Post by aeo24 on 2007-08-07
So i got my 1420(Canadian version)  last Friday i have been trying to get ubuntu on it as of late. My wireless works fine but i realized today that i cannot get a wired connection due to my broadcom 1713 Ethernet card being unrecognized. I have done some research and found those Dell recovery scripts for the 1420n but am unsure of how or if i should use them. This seems to be the last problem i am running into any help would be greatly appreciated. 

Thanks, 
Rich

---

### Post by LMP900 on 2007-08-07
Perhaps this link might help:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/tg3_driver_does_not_recognize_network_controller](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/tg3_driver_does_not_recognize_network_controller)

---

### Post by aeo24 on 2007-08-07
I have seen that page but i am rather new to linux, if you could give me alittle run down of how exactly the dkms works or how i would go about fixing this issue that would be great.

Thanks,
Rich

---

### Post by LMP900 on 2007-08-07
Here's what I did to get my 1420n to connect via a wired connection:

* Open the package manager and remove the installed tg3 driver
* Download and install this [**deb**]("http://linux.dell.com/dkms/debian/dkms_2.0.16.1-1_all.deb")

I can't remember if I had to reboot or not, but I hope that helps.

---

