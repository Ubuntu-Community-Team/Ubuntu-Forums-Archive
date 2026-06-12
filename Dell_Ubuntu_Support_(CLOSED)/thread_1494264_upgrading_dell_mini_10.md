---
title: "upgrading dell mini 10"
date: 2010-05-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chumley348 on 2010-05-26
Hello all,

I am trying to upgrade my dell mini 10 from 8.04 with the 9.10 cd I ordered but can't get it to work.  I can look at the files in the cd.  I tried to restart the computer with the cd installed, but that didn't work.  When I run the updater, it has never said there was an update available for the version of ubuntu.  Does dell have something on it to keep it from updating to a newer version of ubuntu or am I just not doing something right?:confused:

---

### Post by mikewhatever on 2010-05-27
Several things to mention:
1. You can't upgrade from 8.04 directly to 9.10, even with the cd.
2. Dell used to sell netbooks with LPIA port of Ubuntu. That architecture is no longer supported and the cd you have is likely a regular i686. Needless to say, and upgrade from lpia to i686 would not work.
3. Conclusion - upgrading is not an option. You'll have to backup your files and reinstall.

---

### Post by lswartz on 2010-05-27
You will like 9.10 much better than 8.04. Have you considered 10.04? It works well on my Mini 9. Now to your question, your Mini 10 needs a thumb drive to boot 9.10 from & you will need to do an install vs update. My understanding of the Dell version of 8.04 LTS does not give an upgrade path to 10.04 LTS. 

Note. The Mini's won't boot from a USB CD drive. Don't forget to change your boot secquence in your Bios so the USB thumb drive will be 1st. F2 gets you to the bios.

---

### Post by chumley348 on 2010-05-27
Ok, I will do a reinstall.  Whats the best way to do that?, and yes I have another laptop with 9.10/and xp installed on it.  After I erase my hard drive, will it boot from the usb cd drive?, I hope so.

---

### Post by lswartz on 2010-05-27
> **chumley348 said:**
> Ok, I will do a reinstall.  Whats the best way to do that?, and yes I have another laptop with 9.10/and xp installed on it.  After I erase my hard drive, will it boot from the usb cd drive?, I hope so.

No, it won't. The instructions are pretty good here [http://www.ubuntulinux.org/desktop/get-ubuntu/download]("http://www.ubuntulinux.org/desktop/get-ubuntu/download"). You need to create a bootable USB drive.

---

### Post by chumley348 on 2010-05-27
Ok, thanks,  good thing the usb cd drive was cheap.

---

### Post by chumley348 on 2010-05-31
Well thanks to everyone who replied.  I got my dell mini 10 upgraded to 10.04 with no problems and even was able to get the wireless working without any problems.  Looking forward to using 10.04.

Once again, 

THANKS
chumley348:guitar:

---

### Post by lswartz on 2010-06-01
Glad it worked out for you. It sure is a nice OS on my Mini 9. I have been able to watch hulu & youtube without a problem.

---

### Post by Citadel1980 on 2010-06-02
What "exact" version of the Dell Mini 10 do you have and what graphics chip?

I had a Dell Mini 1010 with Intel GMA 500. I used Ubuntu 9.04 but I had to tweak it to get the GMA 500 to work decently - Full screen videos, with no stuttering.

Reason I ask is that the GMA 500 in the Dell Mini 1010 needs the same sort of tweaks for Ubuntu 10.04.

I'm just asking about your hardware in case you have some "secret sauce" that is not generally known.

Just wondering?

---

