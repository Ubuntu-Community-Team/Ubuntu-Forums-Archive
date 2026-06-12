---
title: "Unable to set date and time"
date: 2009-03-04
forum: General Help
---

### Post by terrordrone on 2009-03-04
Hi,

Im on Kubuntu 8.10 KDE 4.2

i am unable to change the date and time in systemsettings -> Date&Time

It gives 3 errors when i click on apply

1) Unable to contact time server : . (the dot is not a typo.. its there in the msg)
2) Can not set date
3) Error setting new time zone

How do i fix this? 

Thanks.

---

### Post by Ripose on 2009-03-04
You have to enter either the name of time server or enter the time and date manually.

---

### Post by terrordrone on 2009-03-08
I would like to set the date and time in the am/pm format and the timezone to gmt + 5 hours 30 mins

how do i do this through the command line.. 


sorry the man page for date command is overwhelming and i am not able to make sense of it :(

thanks

---

### Post by shadyzay on 2009-03-27
Same issue here. I also couldn't use the "Set time and date automatically".

---

### Post by wonko on 2009-03-29
As I understand, this is a problem with the graphical frontend using kdesudo instead of kdesu, as described on [lauchpad]("https://bugs.launchpad.net/ubuntu/+source/kdesudo/+bug/312569").
As a workaround, you can execute the following command in a shell:
```
sudo ntpdate europe.pool.ntp.org
```.

(In my case, however, I had to use the -u switch to force use of an "unprivileged" port, even though I don't use a firewall.)

Btw: You can find a ntp server close to you at [http://www.pool.ntp.org/]("http://www.pool.ntp.org/")

---

