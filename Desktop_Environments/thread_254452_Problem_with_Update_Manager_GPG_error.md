---
title: "Problem with Update Manager: GPG error"
date: 2006-09-10
forum: Desktop Environments
---

### Post by Floren on 2006-09-10
Hi,

From one day to the next without (apparently) touching any system files I get this problem: When I try to run the Update Manager and click on check I get:

[PHP]W: GPG error: http://us.archive.ubuntu.com dapper Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com dapper-updates Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com dapper-backports Release: Unknown error executing gpgv
W: GPG error: http://archive.canonical.com dapper-commercial Release: Unknown error executing gpgv
W: GPG error: http://security.ubuntu.com dapper-security Release: Unknown error executing gpgv[/PHP]

If I try 'sudo apt-get update' from the console, I get the same answer. And I also noticed that all software that I try to install with Synaptic appears as 'Not authenticated'.

Any idea what's wrong?

Thanks,
    Floren

---

### Post by smelly_sox on 2006-09-10
Save this [file]("http://mirror.anl.gov/pub/ubuntu/dists/dapper/Release.gpg") to your desktop.
Open Synaptic. Go to: Settings / Repositories. 
Select the Authentication tab & hit the Import Key File button. Navigate to your desktop & open the file you just saved.
Hope it works 4U.
Regards

---

