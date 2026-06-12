---
title: "Can't update to 10.10! Help?!"
date: 2010-12-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Linuxisawesome12345 on 2010-12-07
I have a Dell mini 10 netbook, running ubuntu 8.04, which came bundled when I purchased the computer last year, and I'm trying to update to 10.10. 
However, I cannot because from following the instructions on the ubuntu website for downloading 10.10 it said to go to the startup disk creator, to install from a USB thumb drive, but I don't have this for some reason and can't do anything without it. What should I do?

Cheers.

---

### Post by ajgreeny on 2010-12-07
Try using unetbootin instead, which I think is available for 8.04.

See [http://ubuntuguide.net/how-to-install-unetbootin-in-ubuntu](http://ubuntuguide.net/how-to-install-unetbootin-in-ubuntu) for details.

---

### Post by Linuxisawesome12345 on 2010-12-07
when trying to update and install UNetbootin, after I typed into terminal "sudo apt-get install unetbootin" it then says that the packages it's trying to install "have unmet dependencies". What does that mean?

---

### Post by fjgaude on 2010-12-07
I think you could go the **UNetbootin** route, because at least in 10.04 and 10.10 the **Startup Disk Creator** has worked too well for many of us.

I ended up buying a USB DVD reader (for $43) and that permitted me to go from 8.04 to 10.10 on my mini 10n with the 1366 x 768 screen. To get that resolution I had to run this script:

```
sudo add-apt-repository ppa:gma500/ppa && sudo apt-get update && sudo apt-get install poulsbo-driver-2d poulsbo-driver-3d poulsbo-config
```

After that 10.10 was perfect in all aspects, from sound, wireless, etc., better than 8.04.

---

### Post by fjgaude on 2010-12-07
> **Linuxisawesome12345 said:**
> when trying to update and install UNetbootin, after I typed into terminal "sudo apt-get install unetbootin" it then says that the packages it's trying to install "have unmet dependencies". What does that mean?

It means you OS doesn't have things that UNetbootin needs. I guess in 8.04 the dependencies are not there. It could be on to the USB DVD reader. Bummer.

---

### Post by Linuxisawesome12345 on 2010-12-07
guess I'll have to get one of those then :| Thanks for the help anyway :)

---

### Post by ugm6hr on 2010-12-09
Do you have access to any other computer at all?
You could create a bootable USB on any Windows or other Ubuntu computer.

---

### Post by davepoth on 2010-12-13
IIRC this isn't a Ubuntu problem, it's an issue with the version of 8.04 Dell use, it's missing all of the stuff you might use to upgrade (update manager is crippled too).

I think in the end I used my mum's PC to make the boot USB.

---

