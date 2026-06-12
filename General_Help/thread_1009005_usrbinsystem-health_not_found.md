---
title: "/usr/bin/system-health: not found"
date: 2008-12-12
forum: General Help
---

### Post by smotsie on 2008-12-12
Hi guys,

I have a clean installation of Kubuntu 8.10 and just got round to setting up proper email forwarding of system reports etc, and noticed I was getting 

/etc/cron.daily/system-health: 8: /usr/bin/system-health: not found

I have searched both my Kubuntu systems and neither have this file, and I have done a dpkg -S system-health which shows nothing.

Does anyone else have this file or know what package it is supposed to be in?

---

### Post by ModelM on 2008-12-12
I think this was in a package called "debian-helper-scripts" which is no longer included.

---

### Post by smotsie on 2008-12-12
> **ModelM said:**
> I think this was in a package called "debian-helper-scripts" which is no longer included.

ah... so does anyone know if the function(s) performed by this script are being done elsewhere? I assume it ran sensors, smartd etc to check that all is ok with a system, but as I re-installed both my systems from clean, only preserving /home I have no easy way of working out what it used to do. I am happy to delete the cron.daily entry if that is all that is needed, but I realy like the feeling that my systems are being monitored every day for dead fans, overheating cpu's etc, and an "I'm happy and healthy" email is safer than hoping for an "I'm unhappy" one when things do go wrong.

---

### Post by kaajinek on 2009-08-27
Hi,
I was going through this trouble in few last days too.
What I have found:

You can download the gzipped archive with system-health here:

[http://mirror.neolabs.kz/ubuntu/pool/universe/d/debian-helper-scripts/](http://mirror.neolabs.kz/ubuntu/pool/universe/d/debian-helper-scripts/)
(I used this one debian-helper-scripts_0.10ubuntu3.tar.gz)

Then you decompress and in /bin/ you can find *system-health* script.
I just copied that into /usr/bin , seems to work now :-)

[FONT=Courier New]wget [http://mirror.neolabs.kz/ubuntu/pool/universe/d/debian-helper-scripts/debian-helper-scripts_0.10ubuntu3.tar.gz](http://mirror.neolabs.kz/ubuntu/pool/universe/d/debian-helper-scripts/debian-helper-scripts_0.10ubuntu3.tar.gz)
tar -xvf debian-helper-scripts_0.10ubuntu3.tar.gz
cd debian-helper-scripts-0.10ubuntu2/bin
sudo cp system-health /usr/bin[/FONT]

---

